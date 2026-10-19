Retour : [[00 Accueil]] · [[Examen PMLE - vue d'ensemble]]

# Domaine 5 : automatiser et orchestrer les pipelines ML (≈ 18 %)
*Automating and orchestrating ML pipelines*

Module : [[M8 Pipelines et MLOps]]

> [!warning] Sous-sections reconstituées
> Plan du guide v3, adapté aux nouveaux noms. À vérifier dans le [PDF officiel](https://services.google.com/fh/files/misc/professional_machine_learning_engineer_exam_guide_english_new.pdf).

## 5.1 Concevoir et implémenter des pipelines d'entraînement
- **Agent Platform Pipelines** (ex-Vertex AI Pipelines) : serverless, exécute des pipelines **Kubeflow Pipelines (KFP)** ou **TFX**.
- Composants : ingestion → validation des données → transformation → entraînement → évaluation → enregistrement → déploiement conditionnel.
- TFX : ExampleGen, StatisticsGen, SchemaGen, ExampleValidator, Transform, Trainer, Evaluator, Pusher.
- Orchestration alternative : **Cloud Composer** (Apache Airflow), pour orchestrer au-delà du ML.
- Cache des étapes, paramètres, artefacts, *lineage* (ML Metadata).

## 5.2 Pipelines de serving et ré-entraînement
- Prédiction par lots planifiée, déploiement automatique si les métriques dépassent un seuil.
- **Déclencheurs de ré-entraînement** : planification (Cloud Scheduler), arrivée de données (Pub/Sub, Eventarc), alerte de dérive venant de Model Monitoring ([[Domaine 6 Monitorer les solutions IA]]).

## 5.3 Suivre et auditer les métadonnées
- ML Metadata, traçabilité des artefacts (quel dataset a produit quel modèle).
- Versionner les données, le code et les modèles (Model Registry).

## 5.4 CI/CD pour le ML (MLOps)
- **Cloud Build** : tests, build des conteneurs, push dans Artifact Registry, compilation et lancement du pipeline.
- Niveaux de maturité MLOps selon Google : niveau 0 (manuel), niveau 1 (pipeline automatisé, entraînement continu), niveau 2 (CI/CD du pipeline lui-même).
- Tests : tests unitaires des composants, tests de validation des données, tests du modèle (seuil de métrique) avant de le promouvoir.

## Quiz
> [!quiz]- Q1. Une équipe ré-entraîne son modèle à la main chaque mois dans un notebook, avec des erreurs fréquentes. Que recommander ?
> A) Écrire une documentation plus détaillée pour l'étape manuelle
> B) Un pipeline Kubeflow sur Agent Platform Pipelines, planifié
> C) Embaucher une personne dédiée à relancer le notebook tous les mois
> D) Ré-entraîner moins souvent pour limiter le nombre d'erreurs
>
> **Réponse : B.** On automatise et on rend reproductible avec un pipeline serverless planifié : c'est le passage au niveau 1 de MLOps.

> [!quiz]- Q2. Le nouveau modèle ne doit être déployé que si son AUC dépasse celle du modèle en production. Comment l'imposer dans le pipeline ?
> A) Une étape d'évaluation suivie d'une condition qui bloque le déploiement
> B) Un e-mail envoyé à l'équipe qui décide ensuite à la main de déployer
> C) Déployer à chaque fois puis revenir en arrière si les clients se plaignent
> D) Comparer les deux modèles une fois par an lors de la revue annuelle
>
> **Réponse : A.** Une étape conditionnelle (`dsl.Condition` / `dsl.If` en KFP, Evaluator et Pusher en TFX) automatise la porte de qualité.

> [!quiz]- Q3. À chaque push sur `main`, l'équipe veut lancer les tests, construire l'image d'entraînement et déclencher le pipeline. Quel outil ?
> A) Cloud Composer avec un DAG Airflow qui s'exécute chaque heure
> B) Un notebook Workbench lancé à la main après chaque push de code
> C) Cloud Build avec un déclencheur sur le dépôt et des étapes définies
> D) Dataflow avec un pipeline Beam qui lit les commits du dépôt Git
>
> **Réponse : C.** Cloud Build est le service CI/CD de Google Cloud, avec des déclencheurs sur les pushes Git.

> [!quiz]- Q4. L'entreprise orchestre déjà des dizaines de workflows de données non ML avec Airflow, et veut y intégrer l'entraînement ML. Que choisir ?
> A) Tout réécrire en TFX pour pouvoir abandonner complètement Airflow
> B) Cloud Composer, avec des opérateurs qui lancent les jobs d'entraînement
> C) Un script cron sur une VM qui appelle chaque workflow l'un après l'autre
> D) Des fonctions Cloud Run qui s'appellent en chaîne sans orchestrateur
>
> **Réponse : B.** Composer (Airflow managé) réutilise l'existant et sait piloter l'Agent Platform. Agent Platform Pipelines reste le choix par défaut pour un pipeline purement ML.

## Ce qu'il faut retenir
- [ ] Je sais dessiner un pipeline ML type, de bout en bout
- [ ] KFP ou TFX, et Agent Platform Pipelines ou Composer : je sais choisir
- [ ] Je connais les déclencheurs de ré-entraînement (planification, données, dérive)
- [ ] Je connais les niveaux de maturité MLOps 0, 1 et 2 selon Google
- [ ] Je sais ce que fait Cloud Build dans le CI/CD du ML

> [!source] Source primaire
> [MLOps: Continuous delivery and automation pipelines in machine learning (Google Cloud)](https://cloud.google.com/architecture/mlops-continuous-delivery-and-automation-pipelines-in-machine-learning)

> [!prof] Une question ?
> Demande à ton agent de t'aider à écrire ton premier pipeline KFP pour le [[Projet fil rouge]].
