Retour : [[00 Accueil]]

# Ressources : ML Engineer et certification Google PMLE

Les ressources de confiance de ce parcours. Les leçons puisent ici, pas dans des souvenirs approximatifs. Chaque entrée indique **à quoi elle sert** (*Use for*).

## Knowledge

### Examen officiel Google
- [Page officielle de la certification Professional Machine Learning Engineer](https://cloud.google.com/learn/certification/machine-learning-engineer)
  Format (50–60 questions, 2 h, 200 $, en anglais ou japonais), inscription, mise à jour 2026 (passage de Vertex AI à Gemini Enterprise Agent Platform). **Use for:** la logistique de l'examen. Voir [[Examen PMLE - vue d'ensemble]].
- [Guide d'examen officiel (PDF, version du 1er juin 2026)](https://services.google.com/fh/files/misc/professional_machine_learning_engineer_exam_guide_english_new.pdf)
  La liste de référence des 6 domaines et de leurs sous-compétences. **Use for:** vérifier la couverture de chaque domaine. C'est la source qui fait foi.
- [Parcours Google Cloud Skills Boost : Machine Learning Engineer (path 17)](https://www.cloudskillsboost.google/paths/17)
  Cours et labs pratiques officiels. **Use for:** la pratique guidée sur Google Cloud en S14–S23.
- [Questions d'exemple officielles](https://docs.google.com/forms/d/e/1FAIpQLSeYmkCANE81qSBqLW0g2X7RoskBX9yGYQu-m1TtsjMvHabGqg/viewform)
  Le style réel des questions. **Use for:** l'auto-évaluation en S16 et S25. Voir [[Quiz d'entraînement PMLE]].
- [Documentation Gemini Enterprise Agent Platform (ex-Vertex AI)](https://docs.cloud.google.com/gemini-enterprise-agent-platform)
  Docs produit : entraînement, endpoints, pipelines, Feature Store, monitoring (lien à vérifier pour la racine exacte). **Use for:** tout détail produit.
- [Correspondance des anciens et nouveaux noms Vertex AI](https://docs.cloud.google.com/gemini-enterprise-agent-platform/vertex-ai-name-changes)
  Table officielle du renommage d'avril 2026. **Use for:** traduire les tutoriels anciens. Voir [[Correspondance des noms Vertex AI]].

### Google : fondamentaux du ML
- [Machine Learning Crash Course (Google)](https://developers.google.com/machine-learning/crash-course)
  Cours gratuit et interactif sur les bases (régression, classification, métriques, données, équité). **Use for:** S4 et la révision des concepts de [[M1 Fondations Python et maths]] et [[M2 ML classique]].
- [Rules of Machine Learning (Martin Zinkevich, Google)](https://developers.google.com/machine-learning/guides/rules-of-ml)
  43 règles d'ingénierie ML tirées de la production chez Google. **Use for:** l'état d'esprit « ingénieur » de l'examen, [[Pièges classiques du ML]] et [[M8 Pipelines et MLOps]].

### Stanford et Coursera
- [Machine Learning Specialization (Andrew Ng, Stanford Online + DeepLearning.AI, Coursera)](https://www.coursera.org/specializations/machine-learning-introduction)
  La porte d'entrée douce vers le ML, en Python. **Use for:** S4–S9 si [[CS229]] paraît trop mathématique.
- [Deep Learning Specialization (DeepLearning.AI, Coursera)](https://www.coursera.org/specializations/deep-learning)
  La théorie vidéo de CS230. **Use for:** S10–S12, [[M3 Deep learning]].
- [[CS229]] : [cs229.stanford.edu](https://cs229.stanford.edu/). Fondations mathématiques du ML. **Use for:** biais/variance, modèles classiques, entretiens.
- [[CS230]] : [cs230.stanford.edu](https://cs230.stanford.edu/). Deep learning orienté projets. **Use for:** stratégie de projet DL et hyperparamètres.
- [[CS231N]] : [cs231n.github.io](https://cs231n.github.io/). Notes de cours sur les CNN. **Use for:** vision et *transfer learning* en S12.
- [[CS224N]] : [web.stanford.edu/class/cs224n](https://web.stanford.edu/class/cs224n/). NLP et Transformers. **Use for:** S13 et S24, LLM.
- [[CS329S]] : [stanford-cs329s.github.io](https://stanford-cs329s.github.io/). Conception de systèmes ML. **Use for:** MLOps et entretiens de *system design*.
- [[CS336]] : [stanford-cs336.github.io](https://stanford-cs336.github.io/). Construire un LLM de zéro. **Use for:** après la certif, pour les postes LLM.
- Vue d'ensemble : [[Parcours Stanford]].

### Livres
- *Designing Machine Learning Systems*, Chip Huyen (O'Reilly, 2022)
  Le livre « métier » du ML Engineer : données, déploiement, dérive, monitoring. **Use for:** domaines 2, 4, 5 et 6 ; entretiens.
- *Hands-On Machine Learning with Scikit-Learn, Keras and TensorFlow*, Aurélien Géron (O'Reilly, 3e éd., 2022)
  La référence pratique en code, de scikit-learn à Keras, par un auteur français. Des traductions françaises existent (*Machine Learning avec Scikit-Learn* et *Deep Learning avec Keras et TensorFlow*, Dunod). **Use for:** [[M2 ML classique]], [[M3 Deep learning]], notebooks d'exercices.
- [*Mathematics for Machine Learning*, Deisenroth, Faisal et Ong (PDF gratuit)](https://mml-book.github.io/)
  Algèbre linéaire, calcul et probabilités, orientés ML. **Use for:** combler une lacune mathématique précise en S3, en consultation et pas en lecture linéaire.

### Agentique avancée (cible AI / Agent Engineer)
- [Anthropic : *Building effective agents*](https://www.anthropic.com/engineering/building-effective-agents)
  Référence sur les motifs de workflows et quand utiliser un agent. **Use for:** [[A4 Orchestration multi-agents]], décisions d'architecture.
- [Anthropic : *Effective context engineering for AI agents*](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents)
  Le contexte comme budget d'attention ; compaction, mémoire, sous-agents. **Use for:** [[A2 Context engineering et outils]].
- [Blog Anthropic Engineering](https://www.anthropic.com/engineering)
  Billets de terrain sur la conception d'outils, la recherche multi-agents et les évals. **Use for:** veille, A2 à A4.
- [Stanford CS329A : Self-Improving AI Agents](https://cs329a.stanford.edu/)
  Cours avancé (automne 2025) sur les agents qui s'améliorent. **Use for:** [[A7 Fine-tuning et RL pour agents]], après la certif.
- [Berkeley RDI : LLM Agents / Agentic AI MOOC](https://rdi.berkeley.edu/education)
  MOOC gratuit (Dawn Song) : raisonnement, frameworks, évaluation, multi-agents, sécurité. **Use for:** [[A3 Évaluer les agents]], [[A6 Sécurité des agents]].
- [Documentation Google ADK](https://google.github.io/adk-docs/)
  Framework d'agents de Google : orchestration, outils, éval, déploiement, A2A. **Use for:** [[A5 Agents en production sur Google Cloud]].
- [Spécification MCP](https://modelcontextprotocol.io/)
  Protocole standard d'outils et de ressources pour agents. **Use for:** A2, A5.
- [OWASP Top 10 for LLM Applications](https://genai.owasp.org/llm-top-10/)
  Taxonomie des risques de sécurité des applications LLM. **Use for:** [[A6 Sécurité des agents]].

### Vidéos et pratique
- [3Blue1Brown : *Essence of Linear Algebra* et *Neural Networks*](https://www.3blue1brown.com/)
  Les meilleures intuitions visuelles en algèbre linéaire et rétropropagation (sous-titres français disponibles). **Use for:** S3 et S10.
- [Kaggle Learn](https://www.kaggle.com/learn)
  Micro-cours pratiques (pandas, ML intro, feature engineering) dans des notebooks prêts à l'emploi. **Use for:** S2 et S9, pratique rapide.

## Wisdom (Communities)

- [r/MachineLearning](https://www.reddit.com/r/MachineLearning/)
  Recherche et industrie, très modéré. **Use for:** la veille et des discussions de fond (plutôt après la certif).
- [r/learnmachinelearning](https://www.reddit.com/r/learnmachinelearning/)
  Bienveillant envers les débutants. **Use for:** poser des questions de débutant, faire relire un projet.
- [r/googlecloud](https://www.reddit.com/r/googlecloud/)
  Praticiens Google Cloud, retours sur les certifications. **Use for:** les retours d'expérience sur l'examen PMLE 2026 et les problèmes de quotas ou de facturation.
- [Google Developer Groups (GDG)](https://gdg.community.dev/)
  Groupes locaux, dont de nombreux chapitres en France (Paris, Lyon, Toulouse, Nantes…), avec des meetups *Build with AI* et des *study jams* de certification. **Use for:** rencontrer des ML Engineers, réseauter pour l'emploi, préparer en groupe.
- [Kaggle (compétitions et discussions)](https://www.kaggle.com/competitions)
  Se confronter à de vrais problèmes, lire les solutions des meilleurs. **Use for:** tester ses compétences en dehors du cours, enrichir le portfolio.
- [Hugging Face Discord](https://huggingface.co/join/discord)
  Communauté open source autour des modèles et des LLM. **Use for:** questions sur les Transformers et les modèles ouverts (S24 et après).
- [Google Cloud Community / Google Developer forums](https://discuss.google.dev/)
  Forum officiel avec des réponses d'employés Google. **Use for:** questions produit sur Agent Platform, BigQuery ML et les pipelines.
- [MLOps Community](https://mlops.community/)
  Slack, podcasts et meetups de praticiens MLOps. **Use for:** comprendre le métier au quotidien et préparer les entretiens.

- [Latent Space (podcast et Discord)](https://www.latent.space/)
  Communauté de référence des *AI Engineers*. **Use for:** veille agentique, retours de terrain, réseau pour l'emploi.

## Gaps
- **Aucune préparation officielle au PMLE en français.** L'examen n'existe qu'en anglais et en japonais. Le cours explique en français et garde les termes anglais (voir [[GLOSSAIRE]]).
- **Le PDF officiel du guide d'examen n'a pas pu être ouvert par l'agent** depuis son environnement. Les pondérations des domaines (~13/16/21/20/18/13 %) viennent de sources secondaires concordantes. À vérifier soi-même sur le PDF.
- **Ressources pas encore à jour du renommage d'avril 2026** : la plupart des cours et examens blancs tiers utilisent encore « Vertex AI ». Il manque un bon examen blanc à jour, à chercher en S24.
- **Agentique** : pas de manuel de référence stable ; le domaine évolue vite. Privilégier les billets d'ingénierie des labos et les docs officielles, et réviser cette liste chaque mois.
- Préférence communautaire de l'élève : pas encore exprimée.
