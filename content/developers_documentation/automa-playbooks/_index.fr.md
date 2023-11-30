+++
archetype = "chapter"
title = "AutomA Playbooks"
weight = 1
+++

## Introduction 

Ce chapitre traite de la documentation sur la partie des playbooks et des questions pour l'ensemble des recommendations mise à disposition des utilisateurs. Vous trouverez le projet [AutomA-Playbooks](https://github.com/Autom-A/AutomA-Playbooks) sur github ainsi que la démarche à suivre pour contribuer sur le projet dans la partie [Contribuer](/fr/developers_documentation/contribute/index.html).


## Arborescence

L'arborescence du dépôt github se découpe selon la forme suivante :
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

A la date du 30 novembre 2023, le projet ressemblait à l'arborescence suivante :
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

Nous avons réfléchis et choisi cette structure de dossier pour permettre une meilleure intégration des futures règles et environnements de durcissement. Le principe de cette structure légèrement conséquente est de permettre une meilleure modularité du projet. 


> Vous voulez contribuer au projet en ajoutant des règles de durcissement pour windows serveur 2022 ?

Vous devez créer l'arborescence (si inexistance), ici `/WINDOWS/SERVER/2022/`. Ensuite, vous devez créer la structure suivante selon les actions de durcissement que vous voulez ajouter. De manière générique, voici les dossiers à créer (dans l'ordre) :

1. **CATEGORY** : Le nom de la catégorie dans laquelle la règle de durcissement s'inscrit. Il est possible que des actions de durcissements puissent être dans plusieurs catégories. Dans ce cas, choississez la catégorie dans laquelle cela serait le plus logique mais en cas de questionnement, vous pouvez ouvrir une issue sur le [projet](https://github.com/Autom-A/AutomA-Playbooks) Github ou par mail à [automa.project@proton.me](mailto:automa.project@proton.me).
2. **REFERENCE** : Le référentiel dans lequel l'action de durcissement est tirée. Nous basons la globalité de nos actions sur les recommandations de l'[ANSSI](https://cyber.gouv.fr/) mais il est possible d'utiliser d'autres référentiels tel que le [CIS](https://www.cisecurity.org/).
3. **LEVEL** : Ce dossier est tiré du système de niveau de l'ANSSI dans son guide de [Recommandations de sécurité relatives à un système GNU/Linux](https://cyber.gouv.fr/publications/recommandations-de-securite-relatives-un-systeme-gnulinux). Dans ce guide, ils proposent une grille de niveaux de durcissement qui permet donc de situer le niveau de l'action de durcissement. Il est nécessaire de bien choisir le niveau de durcissement des règles de durcissements pour permettre une meilleure segmentation et expérience utilisateur. Les niveaux possibles sont les suivants : 
    - 0_MINIMAL
    - 1_INTERMEDIATE
    - 2_REINFORCED
    - 3_HIGH
4. **HARDENING_ACTION** : Le nom de l'action de durcissement précédé d'un identifiant non-nécessairement unique. Dans le cas des *Recommandations de sécurité relatives à un système GNU/Linux*, l'identifiant est constitué d'un **R** suivi d'un nombre, par exemple **R30**. Le but étant de garder la même nomenclature pour un même référentiel.

Lorsque vos dossiers sont créés, il ne manque plus deux fichiers `playbook.yml.j2` et `questions.yml`. Le contenu de ces fichiers sera décrit dans les parties [playbook.yml.j2](/fr/developers_documentation/automa-playbooks/playbook.yml.j2/index.html) et [questions.yml](/fr/developers_documentation/automa-playbooks/questions.yml/index.html).