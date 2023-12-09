---
title: "ANSSI - Linux"
date: 2023-12-08T22:33:38+01:00
draft: false
---

> Dernière mise à jour : 8 décembre 2023

## Debian 12

### Applicabilité

```mermaid
%%{
    init: {
        "theme": "base",
        "themeVariables": {
            "pie1": "#b6d7a8",
            "pie2": "#e06666",
            "pie3": "#ffe599"
        }
    }
}%%
pie title Taux d'applicabilité dans AutomA
    "OUI" : 49
    "NON" : 11
    "?" : 20 
```

Vous trouverez ci-dessous la liste des règles non-applicables :

|Numéro|Niveau|Nom|
|:---:|:---:|---|
|R1|Renforcé|Choisir et configurer son matériel|
|R2|Intermédiaire|Configurer le BIOS/UEFI|
|R3|Intermédiaire|Activer le démarrage sécurisé UEFI|
|R4|Elevé|Remplacer les clés préchargées|
|R28|Intermédiaire|Partitionnement type|
|R64|Renforcé|Configurer les privilèges des services|
|R65|Renforcé|Cloisonner les services|
|R66|Elevé|Durcir les composants de cloisonnement|
|R76|Elevé|Sceller et vérifier l'intégrité des fichiers|
|R77|Elevé|Protéger la base de données des scellés|
|R78|Renforcé|Cloissoner les services réseau|


### Plateforme de test

```mermaid
%%{
    init: {
        "theme": "base",
        "themeVariables": {
            "pie1": "#674ea7",
            "pie2": "#ff00ff",
            "pie3": "#d9d9d9"
        }
    }
}%%
pie title Répartition plateforme de test
    "Docker" : 6
    "VM" : 2
    "?" : 61
```

### Couverture

```mermaid
%%{
    init: {
        "theme": "base",
        "themeVariables": {
            "pie1": "#4285f4",
            "pie2": "#ffff00",
            "pie3": "#00ff00"
        }
    }
}%%
pie title Taux de couverture du référentiel
    "À Faire" : 60
    "En cours" : 1
    "Fait" : 8
```

## Fichiers

Vous trouverez l'ensemble des fichiers qui contiennent les données présentées.

{{% notice title="Fichiers d'avancement" color="#2e738d" icon="fas fa-link" %}}
- [anssi.debian.12.json](/files/anssi.debian.12.json)
{{% /notice %}}