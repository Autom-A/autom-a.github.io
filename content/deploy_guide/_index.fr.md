+++
archetype = "chapter"
title = "3. Guide de déloiement"
weight = 3
+++

Vous trouverez les étapes pour installer AutomA sur votre système d'information. Avant d'expliquer, ces étapes, nous aimerions présenter quelques aspect d'AutomA qui ont un impact sur son installation. AutomA est :
- **Hors-Ligne** : AutomA est prévu pour fonctionner sans connexion à internet, il est alors possible de déployer notre logiciel sur tous vos systèmes d'informations.
- **Sans-Agent** : AutomA utilise Ansible pour fonctionner et donc utilise ssh, aucun agent n'est installé sur vos machines. Seule votre machine d'administration est nécessaire.
- **Exportable** : AutomA permet d'exporter ses configurations pour les appliquer sur d'autres systèmes d'informations. Cela permet par exemple d'installer AutomA sur une machine ayant internet pour profiter des dernières mise à jour tout en déployant les configurations sur d'autre systèmes d'informations.

## Installation Manuelle

### Etape 1 - Prérequis

La liste des logiciels requis pour installer AutomA :
- git
- python3 (>3.9)
- pip3
- un navigateur web à jour

### Etape 2 - Téléchargement du dépôt

Grâce à git, clonez le dépôt du projet :
```bash
git clone https://github.com/Autom-A/AutomA-WebUI.git
```

Un fois effectué, il est nécessaire de télécharger les playbooks :
```bash
cd AutomA-WebUI
git submodule update --init --recursive 
```

### Etape 3 - Téléchargement des dépendances

Le projet a besoin de quelques dépendances python3 :
- ansible-runner
- Flask
- flask-core
- jinja2
- pyyaml

Pour les télécharger, exécutez la commande suivante :
```bash
pip3 install -r requirements.txt
```

### Etape 4 - Lancer le projet

Il suffit de lancer la commande suivante :
```bash
python3 src/main.py
```

Puis ouvrez votre navigateur et tapez dans la bar d'adresse `http://localhost:9123` (avec la configuration par défaut).
