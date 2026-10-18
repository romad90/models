---
semaines: S23
domaine_examen: "[[Domaine 6 Monitorer les solutions IA]]"
---
# M9 Monitoring et IA responsable

Retour : [[00 Accueil]] · Précédent : [[M8 Pipelines et MLOps]] · Suivant : [[M10 IA générative et agents]]

> [!examen] Pourquoi
> Le domaine 6 (environ 13 %) porte sur ce qui arrive **après** le déploiement : un modèle se dégrade silencieusement. Il couvre aussi l'IA responsable, la sécurité et l'explicabilité.

## Thèmes
- *Training-serving skew* et dérive (*drift*) des données et des prédictions ; Model Monitoring d'Agent Platform
- Journalisation, Cloud Monitoring et Cloud Logging, alertes, tableaux de bord
- Explicabilité : attributions de features (Shapley échantillonné, gradients intégrés)
- IA responsable : biais et équité, [principes d'IA de Google](https://ai.google/responsibility/principles/), *model cards*
- Sécurité : IAM au moindre privilège, VPC Service Controls, chiffrement (CMEK), protection des données
- Spécificités de l'IA générative : évaluation, garde-fous, filtres de sécurité

## Compétences visées
- [ ] Configurer une surveillance de dérive sur l'endpoint du [[Projet fil rouge]]
- [ ] Distinguer *skew* et *drift* dans un énoncé d'examen
- [ ] Produire et interpréter des attributions de features
- [ ] Rédiger une *model card* pour ton projet

## Jalon S23
[[Projet fil rouge]] v3 : **de bout en bout**, avec pipeline, endpoint, monitoring et README soigné.

> [!source] Source primaire
> La documentation « Model Monitoring » et « Explainable AI » d'Agent Platform, et *Designing ML Systems*, chap. 8 ([[CS329S]]).

> [!prof] Une question ?
> Demande à ton agent : « la précision de mon modèle baisse en prod, quelle démarche ? »
