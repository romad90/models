---
semaines: S17–S18
domaine_examen: "[[Domaine 2 Collaborer données et modèles]]"
---
# M5 Données et features

Retour : [[00 Accueil]] · Précédent : [[M4 Google Cloud et Agent Platform]] · Suivant : [[M6 Entraîner à l'échelle]]

> [!examen] Pourquoi
> Le domaine 2 (environ 16 %) porte sur la gestion des données et des modèles en équipe : préparation des données à l'échelle, Feature Store, suivi des expériences, versionnement, confidentialité.

## Semaine par semaine
| Sem. | Thème | Services |
|---|---|---|
| S17 | Ingestion et transformation à l'échelle, qualité des données, formats (TFRecord, Parquet, CSV) | BigQuery, Dataflow (Apache Beam), Dataproc (Spark), Pub/Sub |
| S18 | Feature Store, suivi des expériences, Model Registry, notebooks partagés, données sensibles (PII) | Feature Store, Experiments, Model Registry et Workbench d'Agent Platform ; Sensitive Data Protection (ex-DLP) |

## Compétences visées
- [ ] Choisir entre Dataflow, Dataproc et BigQuery pour transformer des données
- [ ] Expliquer comment un Feature Store évite le *training-serving skew*
- [ ] Journaliser des expériences et enregistrer une version de modèle
- [ ] Anonymiser ou masquer des données personnelles avant l'entraînement

> [!source] Source primaire
> Le chapitre « Data » du [parcours 17](https://www.cloudskillsboost.google/paths/17), et *Designing Machine Learning Systems* (Chip Huyen), chap. 3–5, voir [[CS329S]].

Pièges associés : [[Pièges classiques du ML]]

> [!prof] Une question ?
> Demande à ton agent : « Dataflow ou Dataproc ? Donne-moi 3 cas de chaque ».
