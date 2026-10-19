---
module: "[[M2 ML classique]]"
domaine_examen: "[[Domaine 3 Passer du prototype au modèle]] · [[Domaine 6 Monitorer les solutions IA]]"
statut: à faire
---
# Leçon 0003 : métriques de classification

> [!examen] Pourquoi c'est important pour la mission
> L'examen PMLE pose souvent la question « **quelle métrique optimiser ?** » dans un scénario métier (fraude, diagnostic, spam). Choisir la mauvaise métrique, c'est déployer un modèle inutile qui affiche pourtant un beau score.

## Ce que tu sauras faire à la fin
Calculer précision, rappel et F1 à partir d'une matrice de confusion, puis choisir la bonne métrique pour un scénario.

## L'essentiel (connaissances)

**La matrice de confusion** (*confusion matrix*) croise la réalité et la prédiction ([Google MLCC : classification](https://developers.google.com/machine-learning/crash-course/classification)) :

| | Prédit positif | Prédit négatif |
|---|---|---|
| **Réellement positif** | VP (*TP*) | FN (faux négatif, *raté*) |
| **Réellement négatif** | FP (faux positif, *fausse alerte*) | VN (*TN*) |

- **Exactitude** (*accuracy*) = (VP + VN) / total. ⚠️ C'est un **piège** quand les classes sont déséquilibrées : avec 99 % de transactions légitimes, un modèle qui dit toujours « légitime » obtient 99 %.
- **Précision** (*precision*) = VP / (VP + FP). Parmi mes alertes, combien sont vraies ?
- **Rappel** (*recall*) = VP / (VP + FN). Parmi les vrais cas, combien en ai-je trouvé ?
- **F1** = 2 · P · R / (P + R), la moyenne harmonique des deux.

**Seuil de décision** (*decision threshold*) : le modèle sort une probabilité, et on classe « positif » au-dessus du seuil (0,5 par défaut). **Baisser le seuil fait monter le rappel et baisser la précision.** Ce compromis se visualise avec la courbe précision-rappel. L'aire sous cette courbe (**PR-AUC**) est la métrique recommandée pour les classes très déséquilibrées ([scikit-learn : precision-recall](https://scikit-learn.org/stable/auto_examples/model_selection/plot_precision_recall.html)).

**Règle pratique** : un faux négatif coûte cher (fraude ratée, cancer non détecté) → priorité au **rappel**. Une fausse alerte coûte cher (spam qui bloque un vrai mail) → priorité à la **précision**. Tout est résumé dans [[Antisèche métriques]].

## À toi (compétence)

> [!exercice] Exercice : à la main, puis en code
> Un détecteur de fraude analyse 100 transactions : **VP = 8, FN = 2, FP = 12, VN = 78**.
> 1. Calcule **à la main** (papier) : exactitude, précision, rappel, F1.
> 2. Vérifie dans Colab :
> ```python
> import numpy as np
> from sklearn.metrics import confusion_matrix, accuracy_score, precision_score, recall_score, f1_score
>
> y_true = np.array([1]*8 + [1]*2 + [0]*12 + [0]*78)
> y_pred = np.array([1]*8 + [0]*2 + [1]*12 + [0]*78)
>
> print(confusion_matrix(y_true, y_pred))
> print("accuracy ", accuracy_score(y_true, y_pred))
> print("precision", precision_score(y_true, y_pred))
> print("recall   ", recall_score(y_true, y_pred))
> print("f1       ", round(f1_score(y_true, y_pred), 3))
> ```
> **Résultat attendu** : accuracy 0,86 · precision 0,40 · recall 0,80 · F1 ≈ 0,533.
> 3. En une phrase : ce modèle est-il bon pour détecter la fraude ? Qu'est-ce qui te gêne ?

## Rappel actif

> [!quiz]- Q1. 99 % de transactions légitimes. Un modèle prédit toujours « légitime ». Son exactitude ?
> A) 1 %
> B) 50 %
> C) 90 %
> D) 99 %
>
> **Réponse : D.** Il a raison sur les 99 % de cas légitimes, et pourtant il ne détecte **aucune** fraude (rappel = 0). C'est exactement le piège de l'exactitude sur des classes déséquilibrées.

> [!quiz]- Q2. La précision, c'est :
> A) Parmi les positifs prédits, la part de vrais
> B) Parmi les positifs réels, la part de détectés
> C) Parmi toutes les prédictions, la part de correctes
> D) Parmi les négatifs réels, la part de rejetés
>
> **Réponse : A.** Précision = VP / (VP + FP). B est le rappel, C l'exactitude, D la spécificité.

> [!quiz]- Q3. Dépistage du cancer : rater un malade est grave. Que maximiser ?
> A) La précision quitte à rater des cas
> B) L'exactitude car les classes sont toujours équilibrées
> C) Le rappel quitte à multiplier les alertes
> D) La spécificité pour limiter les faux positifs
>
> **Réponse : C.** Quand un faux négatif coûte cher, on maximise le rappel. Les fausses alertes seront écartées par un examen complémentaire.

> [!quiz]- Q4. Tu baisses le seuil de décision de 0,5 à 0,3. Que se passe-t-il, en général ?
> A) La précision monte et le rappel baisse
> B) Le rappel monte et la précision baisse
> C) Les deux métriques montent en même temps
> D) Rien ne change, le modèle est identique
>
> **Réponse : B.** Plus d'exemples passent au-dessus du seuil : on attrape plus de vrais positifs (rappel ↑), mais aussi plus de fausses alertes (précision ↓). Le modèle ne change pas, mais ses **décisions** changent.

> [!quiz]- Q5. (style PMLE) Une banque entraîne un modèle de fraude. 0,1 % des transactions sont frauduleuses. Quelle métrique d'évaluation choisir ?
> A) L'exactitude (accuracy) sur l'ensemble de test
> B) La ROC-AUC sur les données d'entraînement
> C) L'aire sous la courbe précision-rappel (PR-AUC)
> D) La RMSE entre probabilités et labels
>
> **Réponse : C.** Avec une classe positive très rare, la PR-AUC se concentre sur la classe qui compte. L'exactitude est trompeuse, toute métrique calculée sur l'entraînement est biaisée, et la RMSE est une métrique de régression.

> [!source] Source primaire
> [Google MLCC : *Classification* (seuils, matrice de confusion, précision, rappel, ROC/AUC)](https://developers.google.com/machine-learning/crash-course/classification).

> [!prof] Une question ?
> ROC-AUC ou PR-AUC, tu hésites encore ? Demande à ton agent-prof un exemple chiffré.

**Liens** : [[00 Accueil]] · [[GLOSSAIRE]] · [[Antisèche métriques]] · précédente : [[0002-train-validation-test|Leçon 0002]] · suivante : [[0004-premier-modele-bigquery-ml|Leçon 0004 : premier modèle avec BigQuery ML]]
