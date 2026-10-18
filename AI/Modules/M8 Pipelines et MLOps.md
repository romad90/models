---
semaines: S22
domaine_examen: "[[Domaine 5 Automatiser les pipelines]]"
---
# M8 Pipelines et MLOps

Retour : [[00 Accueil]] · Précédent : [[M7 Servir les modèles]] · Suivant : [[M9 Monitoring et IA responsable]]

> [!examen] Pourquoi
> Le domaine 5 (environ 18 %) porte sur l'automatisation de la chaîne : données → entraînement → évaluation → déploiement, de façon reproductible, avec CI/CD et ré-entraînement.

## Thèmes
- Niveaux de maturité MLOps (0, 1, 2) selon Google
- Pipelines d'Agent Platform (ex-Vertex AI Pipelines) avec le SDK **Kubeflow Pipelines (KFP)** ou **TFX**
- Composants, artefacts, métadonnées et lignage
- CI/CD : Cloud Build, Artifact Registry, déclencheurs
- Ordonnancement et déclenchement : Cloud Scheduler, événements Pub/Sub ou Eventarc, ré-entraînement sur dérive
- Orchestration plus large : Cloud Composer (Airflow) : quand l'utiliser plutôt que Pipelines ?

## Compétences visées
- [ ] Écrire un pipeline KFP à 3 composants (préparation, entraînement, évaluation) et l'exécuter
- [ ] Ajouter une condition « déployer seulement si la métrique dépasse le seuil »
- [ ] Déclencher le pipeline à chaque push via Cloud Build
- [ ] Expliquer le niveau de maturité MLOps de ton [[Projet fil rouge]]

> [!source] Source primaire
> [MLOps: Continuous delivery and automation pipelines in machine learning](https://cloud.google.com/architecture/mlops-continuous-delivery-and-automation-pipelines-in-machine-learning) (Google Cloud Architecture Center). À relire avec [Rules of ML](https://developers.google.com/machine-learning/guides/rules-of-ml).

> [!prof] Une question ?
> Demande à ton agent de relire ton pipeline KFP.
