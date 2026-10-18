# ★ Projet fil rouge

Retour : [[00 Accueil]] · Mission : [[MISSION]]

> [!examen] Pourquoi
> La certification ouvre la porte, **le projet décroche l'entretien**. C'est aussi la meilleure révision : tu pratiques chaque domaine de l'examen sur un vrai cas.

## Le principe
Un seul projet, qui grandit avec le cours, public sur GitHub. Choisis un sujet qui t'intéresse et qui utilise un dataset public, par exemple :
- Prédire les retards de vols (BigQuery public datasets)
- Classer des avis clients par sentiment
- Prédire la demande de vélos en libre-service (séries temporelles)

## Jalons
| Jalon | Semaine | Contenu | Domaine |
|---|---|---|---|
| v0 | S1 | Dépôt créé, sujet choisi, dataset identifié | – |
| v1 | S9 | Exploration, baseline et modèle scikit-learn/XGBoost en local, métriques justifiées | [[M2 ML classique]] |
| v1.5 | S15 | Même problème en BigQuery ML : comparer avec la v1 | [[Domaine 1 Solutions IA low-code]] |
| v2 | S20 | Données dans BigQuery, entraînement en job sur Agent Platform, réglage des hyperparamètres | [[Domaine 3 Passer du prototype au modèle]] |
| v2.5 | S21 | Modèle dans le Model Registry, déployé sur un endpoint | [[Domaine 4 Servir et scaler]] |
| v3 | S23 | Pipeline KFP, CI/CD Cloud Build, Model Monitoring, *model card* | [[Domaine 5 Automatiser les pipelines]], [[Domaine 6 Monitorer les solutions IA]] |
| bonus | S24 | Une brique d'IA générative (RAG ou agent) | [[M10 IA générative et agents]] |

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
