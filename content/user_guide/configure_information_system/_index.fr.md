---
title: "Configuration du SI"
date: 2023-12-05T01:08:32+01:00
draft: false
weight: 2
author: Leandre-Bcw, Mijux
---

Nous utilisons Ansible pour propager les actions de durcissment, il est alors nécessaire d'ouvrir un port ssh pour qu'Ansible puisse y effectuer les actions nécessaires. Dans cette page, vous trouverez les informations nécessaire à la mise en place d'un serveur SSH sur une machine linux de type Debian 12.

## Configuration du service SSH

### Vérification du statut

La commande suivante permet de vérifier l'état du service `OpenSSH` :

```bash
sudo systemctl status ssh
```

![OpenSSH Status](/images/user_guide/configure_is/openssh-status.png)

### Activation du service

Si le service est désactivé, la commande suivante permet de le lancer : 

```bash
sudo systemctl start ssh
```

### Service au démarrage

Sur la plus part des systèmes Linux, le service SSH se lance au démarrage. Si ce n'est pas le cas et que vous voulez obtenir ce comportement, la commande suivante permet de l'activer au démarrage de la machine :

```bash
sudo systemctl enable ssh
```

### Configuration du service

Le fichier `/etc/ssh/sshd_config` permet de configurer le daemon SSH. Par défaut, le service s'exécute sur le port TCP/22.

Il est recommandé de :
- Désactiver la connexion du compte `root`
- Désactiver la connexion par mot de passe et préférer la connexion par clé
- Désactiver l'écoute sur l'IPv6 si elle n'est pas utilisée
- Désactiver le `X11 Forwarding`
- Changer le port d'écoute (22 par défaut)

```bash
# OpenSSH config file
Port 50122 # Mettez le port que vous souhaitez
ListenAddress 0.0.0.0 # Ecoute sur l'IPv4

# Pour désactiver l'IPv6, vous devez avoir la ligne suivante commentée
#ListenAddress ::

PubkeyAuthentification yes
PermitRootLogin no
PasswordAuthentification no
PermitEmptyPassowrd no

X11Forwarding no
```

### Génération des clés

Pour générer une paire de clés, SSH intègre la commande suivante :

```bash
ssh-keygen -t ecdsa -b 521 -f /home/user1/.ssh/id_ecdsa_debian12
```

{{% notice style="note" %}}
Il est fortement recommandé de protéger votre clef privée avec un mot de passe !
{{% /notice %}}

Cela permet de générer deux fichiers, `id_ecdsa_debian12` qui contient la clé privée, et `id_ecdsa_debian12.pub` qui contient la clé publique. Ces deux fichiers sont stockés dans le dossier `~/.ssh`. 

### Utilisation des clés

La clé privée de la machine est requise pour utiliser l'authentification par clé dans `AutomA`. Veuillez générer les clés sur la machine hébergeant `AutomA` et ajouter la clé publique correspondante dans le fichier `~/.ssh/authorized_keys` de la machine concernée.

Pour mettre votre clef publique sur la machine distance, il existe plusieurs techniques :

#### SSH-COPY

Vous pouvez utiliser le binaire `ssh-copy` comme suit :
```bash
ssh-copy-id -i ~/.ssh/<your_key>.pub <username>@<ip_address> -p <port>
```

Cette technique ne fonctionne que si le serveur SSH accepte la connexion par mot de passe.

#### Clef USB

Vous pouvez copier votre clef publique sur une clef usb qui est maitrisée. Ensuite, sur la machine de destination, créer le dossier `~/.ssh` et le fichier `~/.ssh/authorized_keys` dans lequel vous copiez le contenu de la clef publique provenant de votre clef USB.

Il est nécessaire d'y appliquer les bonnes permissions.
```bash
chmod 700 /home/user/.ssh
chmod 600 /home/user/.ssh/authorized_keys
chown -R user:user /home/user/.ssh
```