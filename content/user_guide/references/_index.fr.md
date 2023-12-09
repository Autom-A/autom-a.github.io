+++
archetype = "chapter"
title = "Référentiels"
weight = 3
+++

Vous trouverez dans ce chapitre, les informations concernant les référentiels actuellement utilisés ainsi que leur état d'avancement pour chaque environment. Ces pages vous propose des métriques permettant de vous exposer les avancés. Les métriques sont les suivantes :

- **Taux d'applicabilité** : Expose le pourcentage d'actions de durcissement qui seront, à terme, disponibles dans AutomA pour une version d'un système d'exploitation. AutomA ne pouvant agir sur le durcissement matériel (exemple : BIOS/UEFI). Il peut y rester certaines inconnues d'où le troisième taux nommé `?`.
- **Plateforme de test** : Toutes les règles ne pouvant être testées sur un docker, nous exposons ici les pourcentages de tests possible sur docker. Les tests se font sur machine virtuelle lorsque docker ne peut être utilisé.
- **Taux de couverture** : Ce taux espose le pourcentage d'actions effectuées pour un référentiel et une version d'un système d'exploitation donnés.

{{% notice style="info" %}}
Les métriques **Plateforme de test** et **Taux de couverture** sont effectuées sur l'ensemble des recommandations sur lequel nous avons enlevé les règles non-applicables.
{{% /notice %}}

1. Le référentiel [*Recommandations de sécurité relatives à un système GNU/Linux*](https://cyber.gouv.fr/publications/recommandations-de-securite-relatives-un-systeme-gnulinux) de l'ANSSI [⇨ici⇦](/fr/user_guide/references/anssi_linux/index.html)