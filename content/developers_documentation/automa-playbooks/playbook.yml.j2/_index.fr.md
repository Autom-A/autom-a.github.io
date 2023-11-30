---
title: "Fichier playbook.yml.j2"
date: 2023-10-25T16:31:13+02:00
draft: false
---

Les playbooks sont des modèles Jinja de playbooks Ansible. Cela nous permet de rendre les playbooks en fonction des paramètres définis par l'utilisateur.

## Exemple

```yml
---
- name: "R30_Disable_User"
  hosts: "all"

  tasks:

    - name: "Disable user"
      ansible.builtin.user:
        name: {% raw %}"{{ item }}"{% endraw %}
        state: "absent"
      with_items: "{{ used_users }}"
```

Cette règle mélange le rendu AutomA jinja et le rendu Ansible jinja. La variable `used_users` est celle fournie par le `questions.yml`, elle sera donc codée en dur dans le playbook. Pour la variable `item`, elle est entourée de balises jinja `raw` pour forcer l'absence de rendu de cette variable par le moteur de rendu AutomA car c'est une variable rendue par Ansible.