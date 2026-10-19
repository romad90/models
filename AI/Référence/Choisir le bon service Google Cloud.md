Retour : [[00 Accueil]] · [[Examen PMLE - vue d'ensemble]] · Noms : [[Correspondance des noms Vertex AI]]

# Choisir le bon service Google Cloud

## Du moins d'effort au plus de contrôle
```
API pré-entraînées → Gemini / Model Garden (prompt, RAG) → BigQuery ML → AutoML → Custom training
   0 donnée            peu de données                       SQL           données étiquetées   contrôle total
   0 code ML           prompt                               SQL           pas de code ML       code ML complet
```
> [!examen] Règle d'or
> Choisis le niveau **le plus à gauche** qui respecte toutes les contraintes de la question.

## Besoin → service
| Besoin | Service |
|---|---|
| Analyser des images, du texte, de la parole ou de la vidéo de façon générique | API Vision, Natural Language, Speech-to-Text, Translation, Video Intelligence |
| Extraire les champs de documents (factures, formulaires) | Document AI |
| Générer du texte, résumer, chatbot | Gemini via Agent Studio (ex-Vertex AI Studio) |
| Répondre à partir des documents de l'entreprise | RAG : embeddings, Vector Search, Gemini |
| Construire ou héberger des agents | Agent Platform, Agent Runtime (ex-Agent Engine) |
| Modèle ML sur des données BigQuery, équipe SQL | BigQuery ML |
| Prévision de séries temporelles en SQL | BigQuery ML `ARIMA_PLUS` |
| Modèle sur données étiquetées sans expertise ML | AutoML (tabulaire, image, texte, vidéo) |
| Contrôle total, framework et architecture au choix | Custom training (conteneur pré-construit ou personnalisé) |
| Notebook managé | Agent Platform Workbench, Colab Enterprise |
| ETL batch et streaming serverless | Dataflow (Apache Beam) |
| Réutiliser du code Spark/Hadoop existant | Dataproc |
| Messages et événements en streaming | Pub/Sub |
| Entrepôt de données analytique | BigQuery |
| Fichiers, images, artefacts | Cloud Storage |
| Partager et servir des features | Agent Platform Feature Store |
| Suivre des essais d'entraînement | Agent Platform Experiments, TensorBoard |
| Versionner des modèles | Agent Platform Model Registry |
| Prédiction temps réel | Endpoint de l'Agent Platform (en ligne) |
| Scoring de gros volumes | Prédiction par lots, ou `ML.PREDICT` |
| Pipeline ML serverless | Agent Platform Pipelines (KFP / TFX) |
| Orchestrer des workflows ML et non ML (Airflow) | Cloud Composer |
| CI/CD | Cloud Build, Artifact Registry |
| Planifier ou déclencher | Cloud Scheduler, Pub/Sub, Eventarc |
| Détecter le skew et la dérive | Agent Platform Model Monitoring |
| Expliquer les prédictions | Explainable AI, `ML.EXPLAIN_PREDICT` |
| Masquer les PII | Sensitive Data Protection (ex-Cloud DLP) |
| Périmètre de sécurité des données | VPC Service Controls, CMEK, IAM |
| Servir hors de la plateforme | GKE, Cloud Run, TF Lite (edge) |

## Mots-clés de l'énoncé → indice
| L'énoncé dit… | Penche vers… |
|---|---|
| *minimal operational overhead*, *managed* | Serverless ou managé (Dataflow, Pipelines, AutoML) |
| *data analysts*, *SQL* | BigQuery ML |
| *no ML expertise*, *quickly* | API pré-entraînée ou AutoML |
| *custom architecture*, *specific framework* | Custom training |
| *low latency*, *real-time* | Endpoint en ligne, Feature Store en ligne |
| *millions of records*, *nightly* | Prédiction par lots |
| *existing Spark jobs* | Dataproc |
| *existing Airflow* | Cloud Composer |
| *explain*, *regulator* | Explainable AI |
| *PII*, *sensitive* | Sensitive Data Protection |

Liés : [[M4 Google Cloud et Agent Platform]] · [[Domaine 1 Solutions IA low-code]]
