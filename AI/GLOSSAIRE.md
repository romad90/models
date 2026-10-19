# Glossaire ML Engineer

Le langage canonique de ce parcours : machine learning appliqué et Google Cloud, en vue de la certification PMLE. Les leçons, exercices et learning records utilisent ces termes. Le terme anglais est indiqué entre parenthèses, parce que l'examen est en anglais.

> [!note] Comment ce glossaire grandit
> Selon le skill `teach`, un terme n'est promu ici que lorsque tu sais l'**utiliser correctement**. Ce jeu de départ couvre uniquement les leçons [[0001-entrainer-son-premier-modele|0001]] à [[0004-premier-modele-bigquery-ml|0004]]. Il s'enrichit au fil des sessions. Le meilleur exercice : réécrire une définition avec tes propres mots.

Retour : [[00 Accueil]]

## Fondamentaux

**Modèle** (*model*) :
Fonction paramétrée, apprise à partir d'exemples, qui transforme des features en prédiction.
_À éviter_ : algorithme (l'algorithme est la méthode d'apprentissage, le modèle en est le résultat), IA

**Feature** (*feature*) :
Variable d'entrée d'un modèle, notée `X`.
_À éviter_ : attribut, variable explicative, colonne

**Label** (*label*) :
Valeur qu'un modèle apprend à prédire, notée `y`.
_À éviter_ : cible, target, étiquette, variable de sortie

**Apprentissage supervisé** (*supervised learning*) :
Apprentissage d'un modèle à partir d'exemples dont le label est connu.
_À éviter_ : ML classique

**Entraînement** (*training*) :
Ajustement des paramètres d'un modèle pour qu'il colle aux exemples d'entraînement (`fit`, `CREATE MODEL`).
_À éviter_ : apprentissage (trop vague), fitting

**Inférence** (*inference*) :
Utilisation d'un modèle entraîné pour produire des prédictions sur de nouvelles données (`predict`, `ML.PREDICT`).
_À éviter_ : prédiction (désigne le résultat, pas l'acte), scoring

**Hyperparamètre** (*hyperparameter*) :
Réglage choisi **avant** l'entraînement (profondeur d'un arbre, par exemple), que l'entraînement n'ajuste pas.
_À éviter_ : paramètre (les paramètres sont appris pendant l'entraînement)

## Données et généralisation

**Ensemble d'entraînement** (*training set*) :
Exemples utilisés pour l'entraînement.
_À éviter_ : train, données d'apprentissage

**Ensemble de validation** (*validation set*) :
Exemples tenus à l'écart de l'entraînement, utilisés pour choisir les hyperparamètres et comparer les modèles.
_À éviter_ : dev set, jeu de test (c'est un autre ensemble)

**Ensemble de test** (*test set*) :
Exemples jamais utilisés pendant le développement, consultés une seule fois pour estimer la performance finale.
_À éviter_ : holdout (ambigu)

**Généralisation** (*generalization*) :
Capacité d'un modèle à bien prédire sur des données qu'il n'a jamais vues.

**Sur-apprentissage** (*overfitting*) :
Situation où un modèle mémorise le bruit de l'ensemble d'entraînement et généralise mal (grand écart entre score d'entraînement et score de test).
_À éviter_ : surajustement, overfit

**Sous-apprentissage** (*underfitting*) :
Situation où un modèle est trop simple pour capter la relation entre features et label, et obtient de mauvais scores partout.

**Validation croisée** (*k-fold cross-validation*) :
Évaluation où les données sont coupées en *k* blocs qui servent tour à tour d'ensemble de validation, avant de faire la moyenne des *k* scores.
_À éviter_ : CV (seulement à l'écrit, une fois défini)

**Fuite de données** (*data leakage*) :
Présence, pendant l'entraînement, d'une information qui ne sera pas disponible au moment de l'inférence. Elle gonfle artificiellement les scores. Exemple : des données futures dans une série temporelle mélangée.
_À éviter_ : leak, contamination

## Évaluation

**Matrice de confusion** (*confusion matrix*) :
Tableau qui croise labels réels et prédictions en VP, FP, FN et VN.

**Faux positif / faux négatif** (*false positive / false negative*) :
Faux positif : alerte sur un cas réellement négatif. Faux négatif : cas réellement positif que le modèle a raté.
_À éviter_ : erreur de type I / type II (correct, mais moins parlant)

**Exactitude** (*accuracy*) :
Part des prédictions correctes, (VP + VN) / total. Elle est trompeuse quand les classes sont déséquilibrées.
_À éviter_ : précision (faux ami : en français, « précision » désigne ici une autre métrique)

**Précision** (*precision*) :
Parmi les prédictions positives, part de vrais positifs : VP / (VP + FP).

**Rappel** (*recall*) :
Parmi les cas réellement positifs, part détectée : VP / (VP + FN).
_À éviter_ : sensibilité, taux de vrais positifs (synonymes à reconnaître, mais à ne pas utiliser ici)

**F1** (*F1 score*) :
Moyenne harmonique de la précision et du rappel : 2·P·R / (P + R).

**Seuil de décision** (*decision threshold*) :
Probabilité au-dessus de laquelle une prédiction est classée positive. Le baisser fait monter le rappel et baisser la précision.
_À éviter_ : cutoff

**PR-AUC** (*area under the precision-recall curve*) :
Aire sous la courbe précision-rappel, tous seuils confondus. C'est la métrique de référence quand la classe positive est rare.

## Google Cloud

**BigQuery ML** (*BQML*) :
Fonctionnalité de BigQuery qui entraîne, évalue et sert des modèles en SQL (`CREATE MODEL`, `ML.EVALUATE`, `ML.PREDICT`), sans déplacer les données.

**Gemini Enterprise Agent Platform** (*Agent Platform*) :
Plateforme ML et IA unifiée de Google Cloud, nouveau nom de **Vertex AI** depuis avril 2026. Elle regroupe entraînement, AutoML, Model Garden, pipelines, endpoints et monitoring. Voir [[Correspondance des noms Vertex AI]].
_À éviter_ : Vertex AI (ancien nom, encore présent dans beaucoup de ressources : à reconnaître, mais à ne plus utiliser)

**AutoML** :
Service d'Agent Platform qui entraîne automatiquement un modèle de bonne qualité (tabulaire, image, texte) sans écrire de code de modèle.

**Custom training** :
Entraînement sur Agent Platform avec ton propre code (TensorFlow, PyTorch, scikit-learn…) dans un conteneur, avec contrôle total du matériel (GPU/TPU).
_À éviter_ : entraînement personnalisé (ce n'est pas le terme de l'examen)

**Endpoint** :
Point d'accès HTTP managé sur lequel un modèle est déployé pour servir des prédictions **en ligne**, avec une faible latence.
_À éviter_ : API du modèle, serveur
