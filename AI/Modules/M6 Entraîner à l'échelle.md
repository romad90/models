---
semaines: S19–S20
domaine_examen: "[[Domaine 3 Passer du prototype au modèle]]"
---
# M6 Entraîner à l'échelle

Retour : [[00 Accueil]] · Précédent : [[M5 Données et features]] · Suivant : [[M7 Servir les modèles]]

> [!examen] Pourquoi
> Le domaine 3 est **le plus lourd** de l'examen (environ 21 %) : passer d'un notebook à un entraînement reproductible, distribué, sur le bon matériel et avec de bons hyperparamètres.

## Semaine par semaine
| Sem. | Thème | Services |
|---|---|---|
| S19 | Custom training (conteneurs pré-construits ou personnalisés), Artifact Registry, GPU et TPU, entraînement distribué (stratégies de données et de modèle) | Training d'Agent Platform, Cloud Storage |
| S20 | Réglage des hyperparamètres, choix du framework, entraînement efficace (checkpoints, VM Spot/préemptibles) | Hyperparameter tuning d'Agent Platform |

## Compétences visées
- [ ] Empaqueter un script d'entraînement et le lancer en tant que job sur Agent Platform
- [ ] Savoir quand choisir CPU, GPU ou TPU
- [ ] Lancer un job de réglage d'hyperparamètres et lire ses résultats
- [ ] Expliquer *data parallelism* et *model parallelism*

## Jalon S20
[[Projet fil rouge]] v2 : le modèle s'entraîne **sur Google Cloud** via un job, plus seulement dans un notebook.

> [!source] Source primaire
> La documentation « Custom training » d'Agent Platform, et [[CS230]] pour les réglages d'hyperparamètres.

> [!prof] Une question ?
> Demande à ton agent de relire ton Dockerfile d'entraînement.
