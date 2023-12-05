---
title: "Premiers pas"
date: 2023-12-05T00:40:08+01:00
draft: false
weight: 1
author: Leandre-Bcw, Mijux
---

[AutomA](https://github.com/Autom-A) est un projet de durcissement de système d'exploitation automatisé, basé sur les règles et les conseils de références dans le monde de la cybersécurité tel que l'ANSSI. Ce guide utilisateur à pour but de permettre la bonne prise en main de l'interface Web ainsi que la configuration du service SSH.

![Home Page](/images/user_guide/getting_started/home-page.png)

## Sélection de l'environnement

Après avoir cliqué sur `Start` sur la page d'accueil, il vous sera demandé de sélectionner l'environnement des machines qui vont êtres concernées par le durcissement. 

![Environment Selection](/images/user_guide/getting_started/env-selection.png)

{{% notice style="info" %}}
Vous ne pouvez que durcir qu'un seul type d'environnement à la fois
{{% /notice %}}

## Hôte

Il est nécessaire de renseigner les machines à sécuriser dans l'onglet `HOST INVENTORY`. Cet onglet permet de définir l'ensemble des machines à sécuriser.

![Host Inventory Tab](/images/user_guide/getting_started/host-inventory-tab.png)

Vous devez renseigner les informations suivantes :
- **Name** : Un nom arbitraire unique de votre machine
- **IP** : L'adresse IP de votre machine ou son FQDN (exemple : samba.local) 
- **Port** : Le port d'écoute du service SSH de votre machine
- **Connection Method** : Vous avez le choix entre *mot de passe* et *clef*
- **Username** : Le nom d'utilisateur pour la connexion SSH à votre machine
- **Auth** : Le mot de passe ou le chemin d'accès à votre clef privée associée
- **Sudo Username** : Le nom d'utilisateur pour l'élévation de privilège
- **Sudo Password** : Le mot de passe de l'utilisateur ayant les droits d'administration

Ci-dessous, voici un exemple de configuration :

![Host Inventory Tab](/images/user_guide/getting_started/host-inventory-exemple.png)

## Génération des actions

Dans l'onglet `HARDENING ACTION`, une liste d'actions de durcissement est disponible. Ces règles sont classées selon :

- La catégorie de la règle parmi les suivantes :
  - KERNEL
  - LOGGING
  - MEMORY
  - MONITORING
  - NETWORK_STACK
  - PACKAGE_MANAGEMENT
  - PARTITIONING
  - PERMISSIONS
  - SERVICES
  - USERS
- Le niveau de recommandation de la règle
  - MINIMAL
  - INTERMEDIATE
  - REINFORCED
  - HIGH
- Le révérenciel de la règle (ANSSI, NIST, etc ...)

Il est possible de choisir une règle en cliquant dessus et en validant celle-ci : 

![Action Selection](/images/user_guide/getting_started/select-action-1.png)

Certaines règles demandent des informations supplémentaires de la part de l'utilisateur pour définir le comportement adapté.

Par exemple cette règle permet de faire des mise à jours automatiquement sur une fréquence que l'utilisateur peut choisir. Un menu déroulant apparait avec une liste de choix possibles :

![Action Selection With Input](/images/user_guide/getting_started/select-action-2.png)

Ici nous avons choisi `monthly` :

![Action Selection With Input Selected](/images/user_guide/getting_started/select-action-3.png)

## Lancement des actions

Une fois que la configuration est terminée, l'utilisateur doit générer sa configuration en cliquant sur le bouton `GENERATE`.

Il est ainsi possible de lancer les règles sur les machines configurées en appuyant sur le bouton `RUN`. Il est aussi possible de cliquer sur la flèche pour afficher le bouton `DOWNLOAD`, vous permettant alors de récupérer l'ensemble des fichiers pour les lancer manuellement.