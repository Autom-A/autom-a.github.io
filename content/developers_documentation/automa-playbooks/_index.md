+++
archetype = "chapter"
title = "AutomA Playbooks"
weight = 1
+++

## Introduction

This chapter deals with the documentation on the part of the playbooks and the questions for all the recommendations made available to users. You will find the project [AutomA-Playbooks](https://github.com/Autom-A/AutomA-Playbooks) on github as well as the procedure to follow to contribute to the project in the section [Contribute](/developers_documentation/contribute/index.html).

## Tree structure

The tree structure of the github repository is divided into the following form:
```
└── KERNEL
    └── OS
        └── VERSION
            ├── CATEGORY
            │   ├── REFERENCE
            │   │   └── LEVEL
            │   │       └── RXX_ACTION_NAME
            │   │           ├── playbook.yml.j2
            │   │           └── questions.yml
            │   └── REFERENCE2
            │       └── LEVEL2
            │           └── CXX_ACTION_NAME2
            │               ├── playbook.yml.j2
            │               └── questions.yml
            ├── CATEGORY2
            │   └── REFERENCE
            │       └── LEVEL
            │           └── RXX_ACTION_NAME3
            │               ├── playbook.yml.j2
            │               └── questions.yml
            └── CATEGORY3
                └── REFERENCE2
                    └── LEVEL
                        └── RXX_ACTION_NAME4
                            ├── playbook.yml.j2
                            └── questions.yml
```

As of November 30, 2023, the project looked like the following tree:
```
└── LINUX
    └── DEBIAN
        └── 12
            ├── KERNEL
            │   └── ANSSI
            │       └── 1_INTERMEDIATE
            │           └── R11_CONFIGURE_YAMA_LSM
            │               ├── playbook.yml.j2
            │               └── questions.yml
            ├── NETWORK_STACK
            │   └── ANSSI
            │       └── 1_INTERMEDIATE
            │           └── R13_DISABLE_IPV6
            │               ├── playbook.yml.j2
            │               └── questions.yml
            ├── PACKAGE_MANAGEMENT
            │   └── ANSSI
            │       └── 0_MINIMAL
            │           └── R61_PERFORM_REGULAR_UPDATES
            │               ├── playbook.yml.j2
            │               └── questions.yml
            ├── PERMISSIONS
            │   └── ANSSI
            │       ├── 0_MINIMAL
            │       │   └── R54_ACTIVATE_STICKY_BIT
            │       │       ├── playbook.yml.j2
            │       │       └── questions.yml
            │       └── 3_REINFORCED
            │           └── R36_CHANGE_UMASK_VALUE
            │               ├── playbook.yml.j2
            │               └── questions.yml
            └── USERS
                └── ANSSI
                    └── 0_MINIMAL
                        └── R30_DISABLE_UNUSED_USER_ACCOUNTS
                            ├── playbook.yml.j2
                            └── questions.yml
```

We thought about it and chose this folder structure to allow for better integration of future hardening rules and environments. The principle of this slightly substantial structure is to allow better modularity of the project.

> Do you want to contribute to the project by adding hardening rules for Windows Server 2022?

You must create the tree (if it does not exist), here `/WINDOWS/SERVER/2022/`. Then you need to create the following structure according to the hardening actions you want to add. Genericly, here are the folders to create (in order):

1. **CATEGORY** : The name of the category that the hardening rule fits into. It is possible that toughening actions could be in several categories. In this case, choose the category in which it would be the most logical but in case of questions, you can open an issue on the Github [project](https://github.com/Autom-A/AutomA-Playbooks) or by email at [automa.project@proton.me](mailto:automa.project@proton.me).
2. **REFERENCE** : The reference frame in which the hardening action is taken. We base all of our actions on the recommendations of [ANSSI](https://cyber.gouv.fr/) but it is possible to use other repositories such as the [CIS](https://www.cisecurity.org/).
3. **LEVEL** : This file is taken from the ANSSI level system in its guide to [Security Recommendations relating to a GNU/Linux system](https://cyber.gouv.fr/publications/recommandations-de-securite-relatives-un-systeme-gnulinux). In this guide, they offer a grid of hardening levels which therefore allows you to locate the level of hardening action. It is necessary to carefully choose the level of hardening of the hardening rules to enable better segmentation and user experience. The possible levels are as follows:
    - 0_MINIMAL
    - 1_INTERMEDIATE
    - 2_REINFORCED
    - 3_HIGH
4. **HARDENING_ACTION** : The name of the hardening action preceded by a non-necessarily unique identifier. In the case of *Security Recommendations relating to a GNU/Linux system*, the identifier consists of an **R** followed by a number, for example **R30**. The goal is to keep the same nomenclature for the same reference system.

When your folders are created, two files `playbook.yml.j2` and `questions.yml` are no longer missing. The contents of these files will be described in parts [playbook.yml.j2](developers_documentation/automa-playbooks/playbook.yml.j2/index.html) and [questions.yml](/developers_documentation/automa-playbooks/questions.yml/index.html).