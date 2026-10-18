---
semaines: S5–S9
domaine_examen: "[[Domaine 3 Passer du prototype au modèle]]"
---
# M2 ML classique

Retour : [[00 Accueil]] · Précédent : [[M1 Fondations Python et maths]] · Suivant : [[M3 Deep learning]]

> [!examen] Pourquoi
> Beaucoup de questions d'examen portent sur le choix du bon modèle et de la bonne métrique, et sur la détection du sur-apprentissage ou de la fuite de données. En entreprise, le *gradient boosting* sur données tabulaires reste roi.

## Semaine par semaine
| Sem. | Thème | Source |
|---|---|---|
| S5 | Régression linéaire, régression logistique, fonction de coût | [[CS229]] cours 2–3, ou Coursera *ML Specialization* cours 1 |
| S6 | Train/validation/test, biais/variance, régularisation | [[0002-train-validation-test\|Leçon 2]] |
| S7 | Métriques, validation croisée, déséquilibre de classes | [[0003-metriques-de-classification\|Leçon 3]], [[Antisèche métriques]] |
| S8 | Arbres de décision, forêts aléatoires, gradient boosting (XGBoost) | Géron, *Hands-On ML*, chap. 6–7 |
| S9 | k-means, ACP, feature engineering (encodage, normalisation, croisements de features) | ML Crash Course : « Working with data » |

## Compétences visées
- [ ] Choisir entre régression et classification, et la bonne métrique, à partir d'un énoncé métier
- [ ] Diagnostiquer un sur-apprentissage avec les courbes d'apprentissage
- [ ] Entraîner et comparer 3 modèles scikit-learn avec une validation croisée
- [ ] Repérer une fuite de données (*data leakage*), voir [[Pièges classiques du ML]]

## Jalon S9
[[Projet fil rouge]] v1 : un modèle scikit-learn/XGBoost entraîné en local, avec un notebook d'exploration propre.

> [!source] Source primaire
> [Machine Learning Specialization](https://www.coursera.org/specializations/machine-learning-introduction) (Andrew Ng, Stanford Online / DeepLearning.AI), cours 1 et 2 ; [[CS229]] pour approfondir.

> [!prof] Une question ?
> Demande à ton agent : « donne-moi un exercice d'interleaving mêlant métriques et régularisation ».
