---
title: "playbook.yml.j2 file"
date: 2023-10-25T16:31:13+02:00
draft: false
---

The playbooks are jinja templates of Ansible playbooks. This allow us to render playbooks regarding the user probided parameters.

## Example

```yml
---
- name: "Example rule"
  hosts: "all"

  tasks:

    - name: "Disable user"
      ansible.builtin.user:
        name: {% raw %}"{{ item }}"{% endraw %}
        state: "absent"
      with_items: "{{ used_users }}"
```

This rule is mixing AutomA jinja rendering and Ansible jinja rendering. The `used_users` variable is the one provided by the `questions.yml`, thus it will be hardcoded in the playbook. For the `item` variable, it is enclosed in `raw` jinja balises to enforce the no-rendering of this variable by the AutomA renderer as it is an Ansible rendered variable.