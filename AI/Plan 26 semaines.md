# Plan sur 26 semaines (~10 h/semaine)

Retour : [[00 Accueil]] · Mission : [[MISSION]]

Rythme type d'une semaine de 10 h :
- **4 h** de cours (vidéos et lectures de la source primaire du module)
- **3 h** de pratique (leçons, notebooks, labs Google Cloud Skills Boost)
- **2 h** sur le [[Projet fil rouge]]
- **1 h** de rappel actif : refaire les quiz des leçons passées (espacement) et compléter le [[GLOSSAIRE]]

> [!tip] Répétition espacée
> Chaque dimanche, refais les quiz des leçons de **la semaine passée**, puis de **il y a 3 semaines**. C'est ce qui construit la mémoire à long terme (*storage strength*), pas la relecture.

## Phase 1 : Fondations (S1–S4)
| Sem. | Contenu | Module |
|---|---|---|
| S1 | Mise en route : Colab, compte Google Cloud, premier modèle ([[0001-entrainer-son-premier-modele\|leçon 1]]) | [[M0 Mise en route]] |
| S2 | NumPy, pandas, visualisation | [[M1 Fondations Python et maths]] |
| S3 | Algèbre linéaire et probabilités, version intuition | [[M1 Fondations Python et maths]] |
| S4 | Google *Machine Learning Crash Course* (bases), descente de gradient | [[M1 Fondations Python et maths]] |

## Phase 2 : ML classique (S5–S9)
| Sem. | Contenu | Module |
|---|---|---|
| S5 | Régression linéaire et logistique ([[CS229]] cours 2–3) | [[M2 ML classique]] |
| S6 | Split train/validation/test, sur-apprentissage ([[0002-train-validation-test\|leçon 2]]) | [[M2 ML classique]] |
| S7 | Métriques ([[0003-metriques-de-classification\|leçon 3]]), validation croisée | [[M2 ML classique]] |
| S8 | Arbres, forêts aléatoires, gradient boosting (XGBoost) | [[M2 ML classique]] |
| S9 | Non supervisé (k-means, ACP), feature engineering. **Jalon : projet fil rouge v1 en local** | [[M2 ML classique]] |

## Phase 3 : Deep learning (S10–S13)
| Sem. | Contenu | Module |
|---|---|---|
| S10 | Réseaux de neurones, rétropropagation ([[CS230]]) | [[M3 Deep learning]] |
| S11 | TensorFlow/Keras et PyTorch : boucle d'entraînement | [[M3 Deep learning]] |
| S12 | CNN (vision) avec [[CS231N]] en complément, *transfer learning* | [[M3 Deep learning]] |
| S13 | Séquences, embeddings, introduction aux Transformers ([[CS224N]]) | [[M3 Deep learning]] |

## Phase 4 : Google Cloud et domaines d'examen (S14–S23)
| Sem. | Contenu | Module · Domaine |
|---|---|---|
| S14 | Bases de Google Cloud : IAM, Cloud Storage, BigQuery | [[M4 Google Cloud et Agent Platform]] |
| S15 | BigQuery ML ([[0004-premier-modele-bigquery-ml\|leçon 4]]), AutoML, API ML pré-entraînées | [[M4 Google Cloud et Agent Platform]] · [[Domaine 1 Solutions IA low-code]] |
| S16 | Agent Platform : Workbench, Model Garden, Agent Studio | [[M4 Google Cloud et Agent Platform]] · [[Domaine 1 Solutions IA low-code]] |
| S17 | Données : Dataflow, Dataproc, Feature Store, qualité des données | [[M5 Données et features]] · [[Domaine 2 Collaborer données et modèles]] |
| S18 | Expérimentations, Model Registry, notebooks partagés, confidentialité des données | [[M5 Données et features]] · [[Domaine 2 Collaborer données et modèles]] |
| S19 | Custom training, conteneurs, GPU/TPU, entraînement distribué | [[M6 Entraîner à l'échelle]] · [[Domaine 3 Passer du prototype au modèle]] |
| S20 | Réglage des hyperparamètres, choix du framework. **Jalon : projet entraîné sur GCP** | [[M6 Entraîner à l'échelle]] · [[Domaine 3 Passer du prototype au modèle]] |
| S21 | Endpoints en ligne et prédiction par lots, mise à l'échelle, A/B testing | [[M7 Servir les modèles]] · [[Domaine 4 Servir et scaler]] |
| S22 | Pipelines (Kubeflow Pipelines / TFX), CI/CD, ré-entraînement | [[M8 Pipelines et MLOps]] · [[Domaine 5 Automatiser les pipelines]] |
| S23 | Monitoring (dérive, *skew*), IA responsable, explicabilité. **Jalon : projet de bout en bout** | [[M9 Monitoring et IA responsable]] · [[Domaine 6 Monitorer les solutions IA]] |

## Phase 5 : IA générative et examen (S24–S26)
| Sem. | Contenu | Module |
|---|---|---|
| S24 | LLM, RAG, Vector Search, agents, *fine-tuning* et évaluation | [[M10 IA générative et agents]] |
| S25 | Examens blancs, revue des erreurs, fiches [[Choisir le bon service Google Cloud]] | [[M11 Révisions et examen]] |
| S26 | Dernières révisions, puis **passage de l'examen** | [[M11 Révisions et examen]] |

## Après la certification (mois 7–12)
Approfondissement Stanford pour les entretiens et la suite : [[Parcours Stanford]] ([[CS229]] en entier, [[CS224N]], [[CS336]], [[CS329S]]).
