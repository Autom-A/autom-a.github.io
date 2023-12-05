---
title: "Tester les playbooks"
date: 2023-12-01T15:34:38+01:00
draft: false
author: Mijux
---

Les playbooks une fois créés doivent être testé pour vérifier la bonne conformité de l'action de durcissmenent. Pour simplifier le processus, nous mettons à disposition des containers Dokcer permettant alors de tester les playbooks.
Chaque environment doit avoir son propre container à la bonne version. Par exemple même si Debian 11 et Debian 12 sont proches en terme de fonctionnement, il en reste néanmoins nécesseraire de séparer les deux versions en deux images dockers différentes.

{{% notice style="note" %}}
Il est probable que certaines actions de durcissement ne peuvent pas être testées sur un environnement containeurisé. Il sera nécessaire alors d'effectuer les tests sur une machine virtuelle.
{{% /notice %}}

## Images Docker existante

Vous trouverez les images dockers ici. Il sera uniquement nécessaire d'effectuer un pull.


## Images Docker manquante

### Faire une requête

Vous pouvez nous envoyer une demande par mail ou ouvrir une issue ou une discussion sur le Github d'[AutomA](https://github.com/Authom-A).

### Créer l'image

Dans cette partie, nous traiterons l'exemple pour une image de Debian 12, cependant le processus restera identique quel que soit l'environment que vous contenairiser.

#### Prérequis

La liste ci-après décrit l'ensemble des composants nécessaires pour la création d'une image :
- python3
- python3-pip
- python3-venv
- sshpass

ensuite effectuer les commandes : 
```bash
python3 -m venv .venv
source .venv/bin/activate
python3 -m pip install ansible-core
```

#### Dockerfile

Dans un fichier nommé `Dockerfile` : 
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

Pour créer votre image : `docker build -t automa-debian12 .` (N'oubliez pas le point à la fin de la commande !)

Dès que la commande est terminée, vous pouvez instancier votre image en container :
```bash
docker run -d -p 2222:22  --name debian-ssh-container automa-debian12
```

### Fichiers nécessaires

#### inventory.yml

Ce fichier donne la configuration de notre container à Ansible.

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

Le fichier playbook est celui qui sera donnée à Ansible pour qu'il puisse appliquer une règle sur le container. En voici un exemple :

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

### Tester !

Vous pouvez lancer la commande suivante :
```bash
python3 -m ansible playbook -i inventory.yml -l all playbook_example.yml -vvv
```
