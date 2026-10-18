Retour : [[00 Accueil]] · [[Examen PMLE - vue d'ensemble]]

# Correspondance des noms Vertex AI → Agent Platform

Le **22 avril 2026** (Google Cloud Next '26), Google a renommé **Vertex AI** en **Gemini Enterprise Agent Platform**. Les fonctionnalités restent les mêmes : elles ont été reprises et étendues sous le nouveau nom. Le guide d'examen de juin 2026 utilise les **nouveaux** noms, mais la plupart des cours, tutos et examens blancs utilisent les **anciens**. Il faut connaître les deux.

> [!warning] Les noms varient selon les pages Google
> - La [page officielle des changements de nom](https://docs.cloud.google.com/gemini-enterprise-agent-platform/vertex-ai-name-changes) utilise des formes longues, par exemple « Feature Store on Gemini Enterprise Agent Platform » ou « Gemini Enterprise Agent Platform Workbench ».
> - Les [notes de version](https://docs.cloud.google.com/gemini-enterprise-agent-platform/release-notes) utilisent le préfixe court « Agent Platform … ».
>
> Le tableau donne la forme courte. Vérifie la forme exacte sur la page officielle : l'agent n'a vu que des extraits de recherche.

| Ancien nom (Vertex AI) | Nouveau nom (forme courte) | À quoi ça sert |
|---|---|---|
| Vertex AI | Gemini Enterprise Agent Platform (« Agent Platform ») | La plateforme ML/IA unifiée |
| Vertex AI Studio | Agent Studio | Tester des prompts et des modèles génératifs |
| Vertex AI Agent Engine | Agent Runtime | Exécuter et héberger des agents en production |
| Vertex AI Agent Builder | intégré à Agent Platform | Construire des agents |
| Vertex AI Model Garden | Model Garden | Catalogue de modèles (Gemini, open source, partenaires) |
| Vertex AI Workbench | Agent Platform Workbench | Notebooks Jupyter managés |
| Vertex AI Pipelines | Agent Platform Pipelines | Orchestration (Kubeflow Pipelines / TFX) |
| Vertex AI Feature Store | Agent Platform Feature Store | Stocker et servir des features |
| Vertex AI Model Registry | Agent Platform Model Registry | Versionner et gérer les modèles |
| Vertex AI Experiments | Agent Platform Experiments *(non vérifié)* | Suivre les essais d'entraînement |
| Vertex AI Training (custom) | Agent Platform Training *(non vérifié)* | Custom training managé |
| Vertex AI Prediction / Endpoints | Agent Platform Endpoints / Prediction *(non vérifié)* | Prédiction en ligne et par lots |
| Vertex AI Model Monitoring | Agent Platform Model Monitoring *(non vérifié)* | Détecter le *skew* et la dérive (*drift*) |
| Vertex AI Vector Search | Vector Search *(non vérifié)* | Recherche de similarité sur des embeddings |
| Vertex Explainable AI | Explainable AI *(non vérifié)* | Attributions de features |
| Google Agentspace | absorbé dans Gemini Enterprise | Recherche et assistants en entreprise (hors examen) |

> [!tip] Astuce d'examen
> Si une réponse dit « Vertex AI Pipelines » et une autre « Agent Platform Pipelines », c'est **le même service**. Juge la réponse sur l'architecture, pas sur le nom.

Liés : [[M4 Google Cloud et Agent Platform]] · [[Choisir le bon service Google Cloud]]
