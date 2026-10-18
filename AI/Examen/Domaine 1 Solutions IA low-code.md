Retour : [[00 Accueil]] · [[Examen PMLE - vue d'ensemble]]

# Domaine 1 : concevoir des solutions IA low-code (≈ 13 %)
*Architecting low-code AI solutions*

Modules : [[M4 Google Cloud et Agent Platform]] · [[M10 IA générative et agents]] · Leçon : [[0004-premier-modele-bigquery-ml|0004 Premier modèle avec BigQuery ML]]

> [!warning] Sous-sections reconstituées
> Les sous-sections suivent le plan du guide v3 (2024), adapté aux nouveaux noms. Vérifie-les dans le [PDF officiel de juin 2026](https://services.google.com/fh/files/misc/professional_machine_learning_engineer_exam_guide_english_new.pdf).

## 1.1 Construire des modèles avec BigQuery ML
- Choisir le bon type de modèle selon le problème : `LINEAR_REG`, `LOGISTIC_REG`, `BOOSTED_TREE_*`, `KMEANS`, `ARIMA_PLUS` (séries temporelles), `MATRIX_FACTORIZATION` (recommandation), modèles importés (TensorFlow, ONNX) et modèles distants (Gemini via `ML.GENERATE_TEXT`).
- Feature engineering en SQL, clause `TRANSFORM`.
- Prédiction par lots avec `ML.PREDICT`, évaluation avec `ML.EVALUATE`, explications avec `ML.EXPLAIN_PREDICT`.

## 1.2 Utiliser les API ML et les modèles de fondation
- API pré-entraînées : Vision, Natural Language, Translation, Speech-to-Text, Text-to-Speech, Video Intelligence.
- Document AI (formulaires, factures).
- **Model Garden** : choisir un modèle (Gemini, open source comme Gemma ou Llama, partenaires). Agent Studio (ex-Vertex AI Studio) pour prototyper des prompts.
- **RAG** (*Retrieval-Augmented Generation*) avec un moteur de recherche ou Vector Search pour ancrer les réponses dans les données de l'entreprise.

## 1.3 Entraîner avec AutoML
- AutoML pour données tabulaires, image, texte et vidéo, quand on a des données étiquetées mais pas d'expertise ML.
- Préparer les données (format, étiquetage, split), choisir l'objectif, débugger un modèle AutoML.
- Prévision (*forecasting*) tabulaire.

## Arbre de décision rapide
API pré-entraînée (cas générique) → modèle de fondation et prompt ou RAG → BigQuery ML (données dans BigQuery, équipe SQL) → AutoML (données étiquetées, peu d'expertise) → custom training ([[Domaine 3 Passer du prototype au modèle]]).

## Quiz
> [!quiz]- Q1. Un retailer stocke 3 ans de ventes dans BigQuery. Les analystes, qui ne connaissent que SQL, veulent prévoir les ventes par magasin. Que recommander ?
> A) Exporter vers Cloud Storage puis entraîner un modèle LSTM personnalisé
> B) Entraîner un modèle ARIMA_PLUS directement avec BigQuery ML en SQL
> C) Déployer un Llama de Model Garden et lui demander les prévisions
> D) Utiliser l'API Natural Language sur les tickets de caisse des clients
>
> **Réponse : B.** Les données sont déjà dans BigQuery, l'équipe parle SQL et le problème est une série temporelle, donc `ARIMA_PLUS` dans BigQuery ML. A ajoute une charge inutile, C et D ne correspondent pas au problème.

> [!quiz]- Q2. Une banque veut extraire automatiquement les champs de milliers de relevés PDF scannés, rapidement et sans équipe ML. Quelle solution ?
> A) Document AI avec un processeur adapté aux documents de ce type précis
> B) Un CNN entraîné sur mesure avec un entraînement distribué sur des TPU
> C) Un modèle AutoML tabulaire entraîné sur les métadonnées des fichiers PDF
> D) Un pipeline Dataflow qui applique des expressions régulières sur le texte
>
> **Réponse : A.** Document AI est la solution managée prévue pour l'extraction de documents. Elle demande le moins d'efforts et pas d'expertise ML.

> [!quiz]- Q3. Un chatbot interne basé sur Gemini invente des réponses sur la politique RH de l'entreprise. Quelle est la meilleure correction, au coût le plus bas ?
> A) Fine-tuner entièrement Gemini sur tout le web public de ces derniers mois
> B) Augmenter la température du modèle pour obtenir des réponses plus variées
> C) Mettre en place du RAG qui récupère les documents RH pertinents à chaque requête
> D) Remplacer Gemini par un modèle de classification AutoML de type texte
>
> **Réponse : C.** Le RAG ancre les réponses dans les documents à jour, sans réentraînement. Augmenter la température aggrave les hallucinations.

> [!quiz]- Q4. Une startup a 20 000 images étiquetées de défauts de fabrication, pas de data scientist, et doit livrer en 2 semaines. Que choisir ?
> A) API Vision pré-entraînée seule, avec ses étiquettes génériques par défaut
> B) AutoML Image pour entraîner un classifieur sur ses propres étiquettes
> C) Un ResNet codé à la main en PyTorch et entraîné sur un cluster GKE
> D) BigQuery ML avec un modèle de régression logistique sur les pixels
>
> **Réponse : B.** Les classes de défauts sont spécifiques, donc l'API générique ne suffit pas. AutoML Image est le bon compromis sans expertise. C est trop coûteux pour ce délai.

## Ce qu'il faut retenir
- [ ] Je sais citer 5 types de modèles BigQuery ML et leur cas d'usage
- [ ] Je sais quand une API pré-entraînée suffit et quand passer à AutoML
- [ ] Je sais expliquer le RAG et pourquoi il réduit les hallucinations
- [ ] Je connais Model Garden et Agent Studio (ex-Vertex AI Studio)
- [ ] Je sais l'ordre de préférence : API → fondation → BigQuery ML → AutoML → custom

> [!source] Source primaire
> [Documentation BigQuery ML](https://cloud.google.com/bigquery/docs/bqml-introduction) et les labs du [learning path](https://www.cloudskillsboost.google/paths/17).

> [!prof] Une question ?
> Demande à ton agent : « donne-moi 5 scénarios de plus sur le Domaine 1 ».
