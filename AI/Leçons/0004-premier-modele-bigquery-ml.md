---
module: "[[M4 Google Cloud et Agent Platform]]"
domaine_examen: "[[Domaine 1 Solutions IA low-code]]"
statut: à faire
---
# Leçon 0004 : premier modèle avec BigQuery ML

> [!examen] Pourquoi c'est important pour la mission
> Le domaine 1 de l'examen (≈ 13 %) porte sur les **solutions IA low-code**. BigQuery ML est la réponse type quand « les données sont dans BigQuery et l'équipe connaît le SQL ». C'est aussi ton premier contact concret avec Google Cloud.

## Ce que tu sauras faire à la fin
Entraîner, évaluer et utiliser un modèle de classification **uniquement en SQL**, sans déplacer les données.

## L'essentiel (connaissances)

**BigQuery ML (BQML)** permet de créer et d'exécuter des modèles ML avec des requêtes SQL, directement là où vivent les données ([doc officielle : introduction à BigQuery ML](https://cloud.google.com/bigquery/docs/bqml-introduction)). Les trois instructions à retenir :

| Instruction | Rôle | Équivalent scikit-learn |
|---|---|---|
| `CREATE MODEL` | entraînement | `fit` |
| `ML.EVALUATE` | métriques (précision, rappel, ROC-AUC…) | `score` / `sklearn.metrics` |
| `ML.PREDICT` | inférence | `predict` |

Dans `OPTIONS(...)`, `model_type` choisit l'algorithme (`logistic_reg`, `linear_reg`, `boosted_tree_classifier`, `kmeans`…) et `input_label_cols` désigne la colonne label ([référence `CREATE MODEL`](https://cloud.google.com/bigquery/docs/reference/standard-sql/bigqueryml-syntax-create)).

**Gratuit pour commencer** : le [BigQuery sandbox](https://cloud.google.com/bigquery/docs/sandbox) fonctionne sans carte bancaire (les tables y expirent après 60 jours). ⚠️ Hors sandbox, BQML est facturé au volume traité. Le jeu de données de l'exercice est minuscule, mais prends le réflexe de lire l'estimation de volume affichée avant chaque requête ([tarifs](https://cloud.google.com/bigquery/pricing)).

**BQML, AutoML ou custom training ?** En résumé (détails dans [[Choisir le bon service Google Cloud]]) :
- **BigQuery ML** : données dans BigQuery, équipe SQL, modèles classiques, besoin d'aller vite.
- **AutoML** : peu d'expertise ML, données tabulaires, images ou texte, meilleure qualité sans écrire de code de modèle.
- **Custom training** (Agent Platform, ex-Vertex AI) : contrôle total du code, frameworks (TensorFlow, PyTorch), GPU/TPU, architectures sur mesure.

## À toi (compétence)

> [!exercice] Exercice : prédire le revenu en SQL
> Données publiques : recensement américain, label `income_bracket` (`<=50K` ou `>50K`).
> 1. Ouvre la [console BigQuery](https://console.cloud.google.com/bigquery) (sandbox OK) et crée un projet si besoin.
> 2. Crée un dataset :
> ```sql
> CREATE SCHEMA IF NOT EXISTS census;
> ```
> 3. Entraîne sur environ 80 % des lignes. Le découpage par hachage le rend reproductible (voir [[Pièges classiques du ML]]) :
> ```sql
> CREATE OR REPLACE MODEL `census.revenu_model`
> OPTIONS(model_type = 'logistic_reg',
>         input_label_cols = ['income_bracket']) AS
> SELECT age, workclass, education_num, marital_status, occupation,
>        hours_per_week, capital_gain, income_bracket
> FROM `bigquery-public-data.ml_datasets.census_adult_income`
> WHERE MOD(ABS(FARM_FINGERPRINT(CAST(functional_weight AS STRING))), 10) < 8;
> ```
> 4. Évalue sur les 20 % restants, jamais vus :
> ```sql
> SELECT * FROM ML.EVALUATE(MODEL `census.revenu_model`, (
>   SELECT age, workclass, education_num, marital_status, occupation,
>          hours_per_week, capital_gain, income_bracket
>   FROM `bigquery-public-data.ml_datasets.census_adult_income`
>   WHERE MOD(ABS(FARM_FINGERPRINT(CAST(functional_weight AS STRING))), 10) >= 8));
> ```
> 5. Prédis :
> ```sql
> SELECT predicted_income_bracket, income_bracket, age, occupation
> FROM ML.PREDICT(MODEL `census.revenu_model`, (
>   SELECT * FROM `bigquery-public-data.ml_datasets.census_adult_income`
>   WHERE MOD(ABS(FARM_FINGERPRINT(CAST(functional_weight AS STRING))), 10) >= 8))
> LIMIT 20;
> ```
> **Résultat attendu** : une accuracy autour de **0,8**, avec un rappel sur `>50K` nettement plus faible que la précision. Grâce à la [[0003-metriques-de-classification|leçon 3]], tu sais maintenant pourquoi c'est important.
> **Défi** : remplace `logistic_reg` par `boosted_tree_classifier` et compare les métriques.

## Rappel actif

> [!quiz]- Q1. Le principal avantage de BigQuery ML ?
> A) Il entraîne toujours des modèles plus précis qu'AutoML
> B) Il entraîne en SQL sans déplacer les données
> C) Il remplace complètement le travail du data engineer
> D) Il est gratuit quel que soit le volume
>
> **Réponse : B.** BQML amène le ML aux données : pas d'export, pas d'infrastructure, juste du SQL. Il n'est ni toujours meilleur qu'AutoML, ni gratuit à grande échelle.

> [!quiz]- Q2. Quelle fonction renvoie les métriques d'un modèle BQML ?
> A) ML.PREDICT
> B) ML.TRAIN
> C) ML.EXPLAIN
> D) ML.EVALUATE
>
> **Réponse : D.** `ML.EVALUATE` calcule les métriques (précision, rappel, ROC-AUC…). `ML.PREDICT` fait l'inférence. L'entraînement passe par `CREATE MODEL`, pas par une fonction `ML.TRAIN`.

> [!quiz]- Q3. (style PMLE) Des analystes maîtrisent le SQL, les données de churn sont dans BigQuery, il n'y a pas d'équipe ML et il faut un modèle vite. Que recommander ?
> A) BigQuery ML avec un modèle de régression logistique
> B) Custom training PyTorch sur un cluster GPU dédié
> C) Exporter vers Dataproc puis entraîner avec Spark MLlib
> D) Fine-tuning d'un grand modèle depuis le Model Garden
>
> **Réponse : A.** Le scénario coche toutes les cases de BQML : données déjà dans BigQuery, compétences SQL, rapidité, pas d'expertise ML. Les autres options ajoutent de la complexité sans bénéfice.

> [!quiz]- Q4. Dans `CREATE MODEL`, que désigne `input_label_cols` ?
> A) Les colonnes à exclure de l'entraînement
> B) Les colonnes qui partitionnent la table
> C) La colonne cible que l'on prédit
> D) Les colonnes affichées dans les résultats
>
> **Réponse : C.** C'est le label. Toutes les autres colonnes du `SELECT` deviennent des features.

> [!source] Source primaire
> [Tutoriel officiel BigQuery ML : classification sur le jeu *census_adult_income*](https://cloud.google.com/bigquery/docs/logistic-regression-prediction), puis le lab correspondant sur [Google Cloud Skills Boost](https://www.cloudskillsboost.google/paths/17).

> [!prof] Une question ?
> Erreur de permission ou de projet dans la console ? Colle le message à ton agent-prof.

**Liens** : [[00 Accueil]] · [[GLOSSAIRE]] · [[Choisir le bon service Google Cloud]] · [[Domaine 1 Solutions IA low-code]] · précédente : [[0003-metriques-de-classification|Leçon 0003]]
