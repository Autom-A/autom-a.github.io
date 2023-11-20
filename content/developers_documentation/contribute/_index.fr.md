---
title: "Contribuer"
date: 2023-11-10T10:03:04+01:00
draft: false
author: Mijux, Filweyd
---


## Objectif

Ce document a pour objectif de proposer une procédure à suivre pour développer sur le projet [AutomA](https://github.com/Autom-A). Cette procédure s'applique que vous soyez interne ou externe au projet.

## Procédure

### A - ISSUE

Quelque soit le dépôt github sur lequel vous voulez travailler, vous devez créer une issue en y mettant les éléments nécessaires. L'issue doit **impérativement** être rédigée en anglais.
Prenons le cas suivant : vous voulez effectuer une nouvelle recommandation de l'ANSSI par exemple la recommandation R30, voici les champs à remplir :

| Champ | Contenu |
| :---: | ----- |
|Titre |[Make-Rule] R30 - Disable unused user accounts|
|Commentaire|**Todo** : questions.yml + playbook.yml <br> **From** : ANSSI <br> **Rule** : 30 <br> **Level** : Minimal|

De plus si vous êtes dans le projet, vous devez rajouter :
| Champ | Contenu |
| :---: | ----- |
|Assignés|la ou les personnes qui travaillent dessus|
|Labels|[TODO]+[enhancement]|
|Projet| Kanban (penser à mettre en TODO sur le projet dès que créée)|

### B - BRANCHE

#### Cas : Vous travaillez sur le dépôt source du projet

Depuis la page de l'issue, vous pouvez créer une branche de développement associée à celle-ci. Un simple clic sur "Créer une branche" permet de faire afficher une pop-up qui demande plusieurs informations. Vous n'avez pas besoin de changer les informations par défaut.

![CreateBranch1](/images/contribute/img1.png)

![CreateBranch2](/images/contribute/img2.png)

Vous avez maintenant une branche pour développer ! N'oubliez pas de changer de branche (sur vscode un clic en bas à gauche). Voici les commandes à faire dans votre terminal :
```bash
# Pour récupérer les modifications du dépôt, notamment la nouvelle branche
git fetch --all
# Changer de branche de développement
git checkout <nom_de_votre_branche>
# Vérifier
git branch --show-current
```
#### Cas : Vous travaillez sur un fork du projet

Vous devez forker le projet sur votre compte, cela vous permettra d'obtenir les droits pour modifier le code. Une fois sur votre dépôt, vous pouvez soit directement développer sur votre branche *main* ou créer des branches auxiliaires comme nous faisons sur le dépôt officiel.

### C - FUSION

#### Se mettre à jour

##### Cas : Vous travaillez sur le dépôt source du projet

Avant de demander à pousser vos modifications sur la branche principale, vous devez vous assurez que vous n'écraserez pas le travail des autres contributeurs. Pour se faire, vous devez dans un premier temps mettre à jour votre branche au même niveau que la branche main.

Depuis votre branche de développement, effectuer les commandes suivante (dans l'ordre):
```bash
git checkout <votre_branche_de_developpement>
git fetch
git merge origin/main
# Gestion de conflits sur votre branche
# (en ligne de commande ou via votre IDE) 
git push
```

#### Cas : Vous travaillez sur un fork du projet

Vous devez ajouter le dépôt officiel en remote supplémentaire. 
```bash
git remote add source <url_depot>
```

Mettre à jour votre branche :
```bash
git pull source <votre_branche_de_developpement>
```
Vous devez gérer les conflits qui peuvent subvenir tout en veillant à ne pas casser le code déjà existant. Votre dépôt local est maintenant à jour, il faut mettre à jour votre dépôt distant : 
```bash
git push 
```

#### Effectuer la demande de fusion

Depuis l'interface web de github, vous pouvez effectuer une "pull-request" pour fusionner votre branche à la branche main. Lorsque le nombre de relecteurs correspond au nombre minimun, vous pourrez valider la fusion. 