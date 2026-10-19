Retour : [[00 Accueil]] · Leçon : [[0003-metriques-de-classification|0003 Métriques de classification]]

# Antisèche : métriques

## Matrice de confusion (classification binaire)
| | Prédit positif | Prédit négatif |
|---|---|---|
| **Réellement positif** | VP, vrai positif (*TP*) | FN, faux négatif (*FN*) |
| **Réellement négatif** | FP, faux positif (*FP*) | VN, vrai négatif (*TN*) |

## Classification
| Métrique | Formule | Question à laquelle elle répond |
|---|---|---|
| Accuracy (exactitude) | (VP+VN) / total | Quelle part des prédictions est juste ? ⚠️ Trompeuse si les classes sont déséquilibrées |
| **Précision** (*precision*) | VP / (VP+FP) | Quand je dis « positif », ai-je raison ? |
| **Rappel** (*recall*, sensibilité) | VP / (VP+FN) | Quelle part des vrais positifs ai-je trouvée ? |
| Spécificité | VN / (VN+FP) | Quelle part des négatifs ai-je bien rejetée ? |
| **F1** | 2·P·R / (P+R) | Équilibre entre précision et rappel (moyenne harmonique) |
| **ROC-AUC** | Aire sous la courbe du taux de VP en fonction du taux de FP | Capacité à classer les exemples, quel que soit le seuil. Données plutôt équilibrées |
| **PR-AUC** | Aire sous la courbe précision-rappel | Comme ROC-AUC, mais adaptée aux **classes rares** (fraude, maladie) |
| Log loss | −moyenne de [y·log p + (1−y)·log(1−p)] | Qualité des probabilités prédites |

> [!tip] Moyen mnémotechnique
> **P**récision : **P**as de fausse alerte. **R**appel : **R**ien ne m'échappe.

## Quelle métrique selon le coût de l'erreur ?
| Situation | L'erreur coûteuse | On optimise |
|---|---|---|
| Dépistage de cancer, fraude | Rater un vrai cas (FN) | **Rappel** |
| Filtre anti-spam, recommandation risquée | Fausse alerte (FP) | **Précision** |
| Les deux comptent | — | **F1** |
| Classes très déséquilibrées | — | **PR-AUC**, pas l'accuracy |
| Comparer des modèles indépendamment du seuil | — | ROC-AUC ou PR-AUC |

Baisser le seuil de décision augmente le rappel et fait baisser la précision. C'est toujours un compromis (*trade-off*).

## Régression
| Métrique | Particularité |
|---|---|
| **MAE** (erreur absolue moyenne) | Dans l'unité de la cible, robuste aux valeurs aberrantes |
| **MSE** (erreur quadratique moyenne) | Pénalise fortement les grosses erreurs |
| **RMSE** | Racine de la MSE, revient à l'unité de la cible |
| **R²** | Part de la variance expliquée (1 = parfait, 0 = pas mieux que la moyenne) |
| MAPE | Erreur en %, ⚠️ problématique quand les valeurs sont proches de 0 |

## Autres
- **Classement et recommandation** : precision@k, NDCG, MAP.
- **Multi-classe** : macro-moyenne (chaque classe pèse autant) ou micro-moyenne (chaque exemple pèse autant).
- **IA générative** : BLEU, ROUGE (chevauchement de texte), évaluation automatique par un modèle juge, *groundedness*.

Liés : [[Domaine 3 Passer du prototype au modèle]] · [[Pièges classiques du ML]]
