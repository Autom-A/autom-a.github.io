---
title: "Playbooks testing"
date: 2023-12-01T15:34:38+01:00
draft: false
author: Mijux
---


Once the playbooks have been created, they need to be tested to ensure that the hardening action has been carried out correctly. To simplify the process, we provide Dokcer containers for playbook testing.
Each environment must have its own container with the correct version. For example, even if Debian 11 and Debian 12 are close in terms of operation, it's still necessary to separate the two versions into two different docker images.

{{% notice style="note" %}}
It is likely that some hardening actions cannot be tested on a containerized environment. It will therefore be necessary to run the tests on a virtual machine.
{{% /notice %}}

## Existing Docker images

Docker images can be found here. It will only be necessary to perform a pull.


## Missing Docker images

### Make a request

You can send us a request by e-mail or open an issue or discussion on [AutomA](https://github.com/Authom-A)'s Github.

### Creating the image

In this section, we'll deal with the example of a Debian 12 image, but the process will remain the same whatever the environment you're using.

#### Prerequisites

The following list describes all the components required to create an image:
- python3
- python3-pip
- python3-venv
- sshpass

Then execute following commands : 
```bash
python3 -m venv .venv
source .venv/bin/activate
python3 -m pip install ansible-core
```

#### Dockerfile

In the file named `Dockerfile`:
```Dockerfile
FROM debian:12

RUN apt-get update -y && \
    apt-get install openssh-server sudo python3 -y

RUN sed -i "s/#PermitRootLogin prohibit-password/PermitRootLogin Yes/" /etc/ssh/sshd_config

RUN useradd -m -s /bin/bash user && \
    echo 'user:password!' | chpasswd && \
    echo 'root:password!' | chpasswd && \
    service ssh restart

EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]
```

To build your image: `docker build -t automa-debian12 .` (Do not forget the dot at the end !)

Once your build command is finished, you can instanciate it with:
```bash
docker run -d -p 2222:22  --name debian-ssh-container automa-debian12
```
### Required files

#### inventory.yml

This file gives our container configurations to Ansible.
```yml
all:
  hosts:
    docker-debian12:
      ansible_host: 127.0.0.1
      ansible_port: 2222
      ansible_user: user
      ansible_password: password!
      ansible_become: yes
      ansible_become_method: sudo
      ansible_become_user: root
      ansible_become_password: password!
```

#### playbook.yml

The playbook file is the one that will be given to Ansible so that it can apply a rule to the container. Here's an example:
```yml
---
- name: "Disable unused user accounts"
  hosts: "all"

  tasks:

    - name: "List all users"
      ansible.builtin.getent:
        database: "passwd"
        split: ":"
      register: "all_users"

    - name: "Disable user"
      ansible.builtin.user:
        name: "{{ item }}"
        state: "absent"
      with_items: "{{ all_users.ansible_facts.getent_passwd }}"
      when:
        - item not in ['root','user','_apt','sshd']
```

### Testing !

You can execute the following command:
```bash
python3 -m ansible playbook -i inventory.yml -l all playbook_example.yml -vvv
```
