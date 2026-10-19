# ★ Projet fil rouge

Retour : [[00 Accueil]] · Mission : [[MISSION]]

> [!examen] Pourquoi
> La certification ouvre la porte, **le projet décroche l'entretien**. C'est aussi la meilleure révision : tu pratiques chaque domaine de l'examen sur un vrai cas.

## Le principe
Un seul projet, qui grandit avec le cours, public sur GitHub : **un agent en production qui s'appuie sur un modèle ML que tu as entraîné toi-même**, exposé comme outil. C'est exactement le profil recherché : un AI Engineer qui maîtrise à la fois le ML et l'agentique. Exemples :
- Un agent d'analyse de vols qui appelle ton modèle de prédiction de retards (BigQuery public datasets)
- Un agent de support qui route les tickets grâce à ton classifieur de sentiment ou de catégorie
- Un agent de planification qui interroge ton modèle de prévision de demande de vélos (séries temporelles)

Côté agent : ADK, outil MCP vers ton endpoint, éval ([[A3 Évaluer les agents]]), défenses ([[A6 Sécurité des agents]]), traces et coûts ([[A5 Agents en production sur Google Cloud]]).

## Jalons
| Jalon | Semaine | Contenu | Domaine |
|---|---|---|---|
| v0 | S1 | Dépôt créé, sujet choisi, dataset identifié | – |
| v1 | S9 | Exploration, baseline et modèle scikit-learn/XGBoost en local, métriques justifiées | [[M2 ML classique]] |
| v1.5 | S15 | Même problème en BigQuery ML : comparer avec la v1 | [[Domaine 1 Solutions IA low-code]] |
| v2 | S20 | Données dans BigQuery, entraînement en job sur Agent Platform, réglage des hyperparamètres | [[Domaine 3 Passer du prototype au modèle]] |
| v2.5 | S21 | Modèle dans le Model Registry, déployé sur un endpoint | [[Domaine 4 Servir et scaler]] |
| v3 | S23 | Pipeline KFP, CI/CD Cloud Build, Model Monitoring, *model card* | [[Domaine 5 Automatiser les pipelines]], [[Domaine 6 Monitorer les solutions IA]] |
| v4 | S17 | L'agent ADK appelle ton endpoint comme outil MCP, avec un jeu d'éval en CI | [[A5 Agents en production sur Google Cloud]], [[A3 Évaluer les agents]] |
| v5 | S24 | Agent déployé (Agent Runtime ou Cloud Run), red team, tableau de bord coût et latence, option de distillation | [[A6 Sécurité des agents]], [[A7 Fine-tuning et RL pour agents]] |

## Le README qui fait la différence
- Le problème métier, en 3 lignes
- Un schéma d'architecture
- Les résultats chiffrés et le choix des métriques
- Les coûts Google Cloud, et comment les limiter
- Ce que tu ferais ensuite (montre ton recul)

> [!warning] Coûts
> Crée un **budget avec alerte** dès S14, et supprime les endpoints après usage : un endpoint facture même sans trafic.

> [!prof] Une question ?
> Demande à ton agent de faire une revue de ton dépôt à chaque jalon.
