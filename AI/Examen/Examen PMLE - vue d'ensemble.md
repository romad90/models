Retour : [[00 Accueil]] · [[Plan 26 semaines]]

# Examen PMLE : vue d'ensemble

> [!examen] En une phrase
> Le **Google Cloud Professional Machine Learning Engineer** valide ta capacité à concevoir, construire, déployer et surveiller des solutions ML sur Google Cloud. C'est un examen de **jugement d'architecture**, pas de code.

## Format
| Élément | Détail |
|---|---|
| Durée | 2 heures |
| Questions | 50 à 60 QCM, à réponse unique ou multiple (*multiple choice / multiple select*) |
| Prix | 200 $ (taxes en sus) |
| Langues | Anglais, japonais (pas de français : apprends le vocabulaire anglais du [[GLOSSAIRE]]) |
| Passage | En ligne surveillé (*online-proctored*) ou en centre Pearson VUE |
| Prérequis | Aucun |
| Expérience recommandée | 3 ans et plus en industrie, dont au moins 1 an sur Google Cloud |
| Code | Pas évalué directement, mais il faut savoir **lire** des extraits de Python et de SQL |

## Validité et renouvellement
Les certifications Professional ont une durée de validité limitée, et il faut repasser l'examen pour renouveler. Certaines sources disent 2 ans, d'autres 3 ans : **la FAQ officielle fait foi**, voir la [FAQ renouvellement](https://support.google.com/cloud-certification/answer/9907853).

## Liens officiels
- [Page de la certification](https://cloud.google.com/learn/certification/machine-learning-engineer)
- [Guide d'examen (PDF, version de juin 2026)](https://services.google.com/fh/files/misc/professional_machine_learning_engineer_exam_guide_english_new.pdf)
- [Learning path Cloud Skills Boost](https://www.cloudskillsboost.google/paths/17) (labs pratiques)
- [Questions d'exemple officielles](https://docs.google.com/forms/d/e/1FAIpQLSeYmkCANE81qSBqLW0g2X7RoskBX9yGYQu-m1TtsjMvHabGqg/viewform)

## Les 6 domaines et leurs pondérations
> [!warning] À vérifier
> Les pondérations ci-dessous viennent de **sources secondaires concordantes** (guides tiers de 2026 qui citent le guide de juin 2026). L'agent n'a pas pu ouvrir le PDF officiel. Vérifie-les dans le PDF. Le total publié fait 101 %, à cause des arrondis.

| # | Domaine | Poids ≈ | Module(s) |
|---|---|---|---|
| 1 | [[Domaine 1 Solutions IA low-code]] (*Architecting low-code AI solutions*) | 13 % | [[M4 Google Cloud et Agent Platform]], [[M10 IA générative et agents]] |
| 2 | [[Domaine 2 Collaborer données et modèles]] (*Collaborating within and across teams to manage data and models*) | 16 % | [[M5 Données et features]] |
| 3 | [[Domaine 3 Passer du prototype au modèle]] (*Scaling prototypes into ML models*) | 21 % | [[M6 Entraîner à l'échelle]] |
| 4 | [[Domaine 4 Servir et scaler]] (*Serving and scaling models*) | 20 % | [[M7 Servir les modèles]] |
| 5 | [[Domaine 5 Automatiser les pipelines]] (*Automating and orchestrating ML pipelines*) | 18 % | [[M8 Pipelines et MLOps]] |
| 6 | [[Domaine 6 Monitorer les solutions IA]] (*Monitoring AI solutions*) | 13 % | [[M9 Monitoring et IA responsable]] |

> [!warning] Renommage d'avril 2026
> Vertex AI est devenu **Gemini Enterprise Agent Platform**. Le guide de juin 2026 utilise les nouveaux noms, alors que la plupart des cours et des examens blancs utilisent encore les anciens. Voir [[Correspondance des noms Vertex AI]].

## Stratégie pour répondre aux questions
1. **Repère les mots-clés de contrainte** : *minimize operational overhead*, *quickly*, *cost-effective*, *low latency*, *explainability*, *data must stay in region*, *no ML expertise*. Ce sont eux qui désignent la bonne réponse.
2. **Service managé d'abord** : à résultat égal, Google préfère la solution gérée (*managed*) et native à Google Cloud plutôt que du sur-mesure sur Compute Engine ou GKE.
3. **Le moins d'efforts d'abord** : API pré-entraînée, puis BigQuery ML ou AutoML, puis custom training. Ne monte d'un cran que si la question l'exige (modèle spécifique, contrôle fin, framework précis).
4. **Élimine** d'abord les réponses qui violent une contrainte : latence, coût, sécurité, données sensibles.
5. **Données dans BigQuery et équipe SQL** : BigQuery ML est très souvent la réponse.
6. Gère ton temps : environ 2 minutes par question. Marque les questions douteuses pour y revenir (*mark for review*).

## Préparation
- Révisions finales : [[M11 Révisions et examen]] · [[Quiz d'entraînement PMLE]]
- Fiches : [[Choisir le bon service Google Cloud]] · [[Antisèche métriques]] · [[Pièges classiques du ML]]

> [!prof] Une question ?
> Demande à ton agent-prof de te générer des questions sur ton domaine le plus faible.
