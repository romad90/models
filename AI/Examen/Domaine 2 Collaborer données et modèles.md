Retour : [[00 Accueil]] · [[Examen PMLE - vue d'ensemble]]

# Domaine 2 : collaborer au sein des équipes pour gérer données et modèles (≈ 16 %)
*Collaborating within and across teams to manage data and models*

Module : [[M5 Données et features]] · Leçons : [[0002-train-validation-test|0002 Train / validation / test]]

> [!warning] Sous-sections reconstituées
> Plan du guide v3, adapté aux nouveaux noms. À vérifier dans le [PDF officiel](https://services.google.com/fh/files/misc/professional_machine_learning_engineer_exam_guide_english_new.pdf).

## 2.1 Explorer et prétraiter les données à l'échelle de l'organisation
- Choisir le stockage : Cloud Storage (fichiers, images), BigQuery (tabulaire, analytique), Spanner ou Cloud SQL (transactionnel).
- Traitement : **Dataflow** (Apache Beam, batch et streaming), **Dataproc** (Spark/Hadoop), BigQuery SQL, Dataprep.
- Formats : TFRecord, Parquet, CSV, Avro.
- Gestion des données sensibles : **Sensitive Data Protection** (ex-Cloud DLP) pour masquer les PII, IAM, chiffrement (CMEK), VPC Service Controls.
- **Feature Store** de l'Agent Platform (ex-Vertex AI Feature Store) : partager les features entre équipes et éviter le *training-serving skew*.

## 2.2 Prototyper des modèles dans des notebooks
- Choisir le bon environnement : **Agent Platform Workbench** (ex-Vertex AI Workbench), Colab Enterprise, Dataproc avec Spark.
- Bonnes pratiques de sécurité des notebooks : comptes de service, pas de clés en dur.
- Lire les données BigQuery depuis un notebook.

## 2.3 Suivre et lancer des expérimentations ML
- **Experiments** de l'Agent Platform et TensorBoard : comparer des runs, des paramètres et des métriques.
- **Model Registry** : versionner, étiqueter, promouvoir des modèles.
- Métadonnées ML (*ML Metadata*) et traçabilité (*lineage*).
- Gérer les modèles génératifs : comparer des prompts, évaluer.

## Quiz
> [!quiz]- Q1. Deux équipes recalculent séparément la feature « panier moyen 30 jours », avec des résultats différents en entraînement et en production. Que faire ?
> A) Centraliser la feature dans Feature Store pour l'entraînement et le serving
> B) Demander aux deux équipes de documenter leur code dans un wiki commun
> C) Doubler la taille du jeu d'entraînement pour lisser les différences
> D) Passer toutes les données de BigQuery vers des fichiers CSV partagés
>
> **Réponse : A.** Une seule définition, servie en entraînement et en ligne, élimine le *training-serving skew*. C'est le rôle même du Feature Store.

> [!quiz]- Q2. Un dataset clients contient des numéros de carte bancaire. L'équipe ML doit l'utiliser sans exposer les PII. Que recommander ?
> A) Laisser les données telles quelles et limiter l'accès aux seuls notebooks
> B) Supprimer manuellement les colonnes sensibles dans un tableur partagé
> C) Chiffrer le bucket et donner la clé à tous les data scientists du projet
> D) Utiliser Sensitive Data Protection pour détecter et masquer les PII
>
> **Réponse : D.** Sensitive Data Protection (ex-Cloud DLP) détecte et désidentifie automatiquement les PII, à l'échelle.

> [!quiz]- Q3. Il faut nettoyer 10 To de logs qui arrivent en continu et en batch, avec un seul code et sans gérer de cluster. Quel service ?
> A) Dataproc avec un cluster Spark dimensionné et maintenu par l'équipe
> B) Dataflow avec un pipeline Apache Beam pour le batch et le streaming
> C) Un script Python sur une VM Compute Engine lancé par une tâche cron
> D) Agent Platform Workbench avec un notebook exécuté chaque nuit à la main
>
> **Réponse : B.** Dataflow est serverless, et Beam unifie le batch et le streaming. Dataproc demande de gérer des clusters, sauf s'il y a déjà du code Spark à réutiliser.

> [!quiz]- Q4. Un data scientist veut comparer 40 runs d'entraînement (hyperparamètres et métriques) et partager les résultats avec son équipe. Que choisir ?
> A) Un tableur partagé rempli à la main après chaque run d'entraînement
> B) Des captures d'écran des courbes stockées dans un bucket Cloud Storage
> C) Agent Platform Experiments avec TensorBoard pour suivre et comparer les runs
> D) Des logs imprimés dans Cloud Logging puis filtrés avec des requêtes manuelles
>
> **Réponse : C.** Experiments est conçu pour suivre et comparer les runs, et partager les résultats.

## Ce qu'il faut retenir
- [ ] Dataflow, Dataproc ou BigQuery : je sais lequel choisir
- [ ] Je sais ce qu'est le *training-serving skew* et comment le Feature Store l'évite
- [ ] Je connais Sensitive Data Protection (DLP), CMEK, VPC-SC et IAM pour les données ML
- [ ] Je sais à quoi servent Experiments, Model Registry et ML Metadata
- [ ] Workbench ou Colab Enterprise : je sais quand utiliser l'un ou l'autre

> [!source] Source primaire
> [Rules of Machine Learning (Google)](https://developers.google.com/machine-learning/guides/rules-of-ml), parties sur les données et les features.

> [!prof] Une question ?
> Demande à ton agent de t'expliquer le *training-serving skew* sur ton [[Projet fil rouge]].
