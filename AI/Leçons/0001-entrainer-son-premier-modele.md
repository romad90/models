---
module: "[[M0 Mise en route]]"
domaine_examen: "[[Examen PMLE - vue d'ensemble]]"
statut: à faire
---
# Leçon 0001 : entraîner son premier modèle

> [!examen] Pourquoi c'est important pour la mission
> Tout le travail d'un ML Engineer (pipelines, déploiement, monitoring sur Google Cloud) tourne autour d'une seule boucle : **entraîner** un modèle, puis s'en servir pour **prédire**. Tu la fais tourner aujourd'hui, en 15 minutes.

## Ce que tu sauras faire à la fin
Entraîner un vrai classifieur sur de vraies données médicales, puis mesurer sa performance. Trois lignes de code utiles.

## L'essentiel (connaissances)

**Le ML, c'est apprendre une fonction à partir d'exemples.** Au lieu d'écrire les règles à la main (`if taille > 3 cm and ...`), tu donnes des exemples et l'algorithme trouve la fonction qui relie entrée et sortie ([Google ML Crash Course](https://developers.google.com/machine-learning/crash-course), [CS229, cours 1](https://cs229.stanford.edu/)).

Le vocabulaire minimal (voir [[GLOSSAIRE]]) :
- **Feature** (*caractéristique*) : une variable d'entrée. Ici, les mesures d'une tumeur. On la note `X`.
- **Label** (*étiquette*) : la valeur à prédire. Ici, maligne ou bénigne. On le note `y`.
- **Apprentissage supervisé** (*supervised learning*) : apprendre à partir d'exemples dont on connaît le label.

La boucle de scikit-learn, la même pour presque tous les modèles ([guide scikit-learn](https://scikit-learn.org/stable/getting_started.html)) :

```
model.fit(X_train, y_train)   # entraînement : ajuster les paramètres aux exemples
model.predict(X_test)         # inférence : prédire sur des exemples jamais vus
```

On évalue toujours sur des données **que le modèle n'a pas vues pendant l'entraînement**. Sinon, on mesure sa mémoire, pas sa capacité à généraliser. La [[0002-train-validation-test|leçon 2]] approfondit ce point.

## À toi (compétence)

> [!exercice] Exercice : ton premier classifieur
> 1. Ouvre [Google Colab](https://colab.research.google.com/) → *Nouveau notebook*. Rien à installer.
> 2. Colle ce code dans une cellule, puis exécute-le (Maj+Entrée) :
> ```python
> from sklearn.datasets import load_breast_cancer
> from sklearn.model_selection import train_test_split
> from sklearn.preprocessing import StandardScaler
> from sklearn.pipeline import make_pipeline
> from sklearn.linear_model import LogisticRegression
> from sklearn.metrics import accuracy_score
>
> # 1. Données : 569 tumeurs, 30 features, label 0 = maligne, 1 = bénigne
> X, y = load_breast_cancer(return_X_y=True)
> print(X.shape, y.shape)
>
> # 2. On garde 20 % des exemples de côté pour l'évaluation
> X_train, X_test, y_train, y_test = train_test_split(
>     X, y, test_size=0.2, random_state=42, stratify=y)
>
> # 3. Modèle : normalisation + régression logistique
> model = make_pipeline(StandardScaler(), LogisticRegression())
> model.fit(X_train, y_train)            # entraînement
>
> # 4. Inférence sur les données jamais vues
> y_pred = model.predict(X_test)
> print("Accuracy test :", accuracy_score(y_test, y_pred))
> ```
> 3. **Résultat attendu** : `(569, 30) (569,)` puis une accuracy autour de **0,95 à 0,99**. Si tu obtiens ça, ton modèle classe correctement plus de 95 % des tumeurs qu'il n'a jamais vues.
> 4. **Bonus** : remplace `LogisticRegression()` par `DecisionTreeClassifier()` (`from sklearn.tree import DecisionTreeClassifier`). L'accuracy monte-t-elle ou baisse-t-elle ?

## Rappel actif
Réponds de tête **avant** d'ouvrir chaque réponse.

> [!quiz]- Q1. Qu'est-ce qu'un label ?
> A) Une colonne d'entrée du modèle
> B) Un réglage choisi avant l'entraînement
> C) La valeur cible à prédire
> D) Le nom du fichier source
>
> **Réponse : C.** Le label (`y`) est ce que le modèle apprend à prédire. Les colonnes d'entrée sont les features (`X`). Un réglage choisi avant l'entraînement s'appelle un hyperparamètre.

> [!quiz]- Q2. Que fait `model.fit(X_train, y_train)` ?
> A) Il ajuste les paramètres aux exemples
> B) Il prédit les labels des exemples
> C) Il découpe les données en deux
> D) Il affiche la précision du modèle
>
> **Réponse : A.** `fit` est l'entraînement : l'algorithme ajuste les paramètres internes du modèle pour coller aux exemples. `predict` fait l'inférence, et `train_test_split` fait le découpage.

> [!quiz]- Q3. Pourquoi évaluer sur `X_test` plutôt que sur `X_train` ?
> A) Parce que X_test contient beaucoup plus de lignes
> B) Parce que la bibliothèque l'impose toujours par défaut
> C) Parce que X_train est déjà beaucoup trop normalisé
> D) Parce que le modèle ne l'a pas vu
>
> **Réponse : D.** Un modèle évalué sur ses données d'entraînement mesure sa mémoire. Seules des données inédites disent s'il **généralise**, c'est-à-dire s'il marchera en production.

> [!quiz]- Q4. L'apprentissage supervisé, c'est :
> A) Apprendre sans aucun exemple étiqueté disponible
> B) Apprendre une fonction depuis exemples étiquetés
> C) Écrire les règles à la main
> D) Mémoriser les données sans rien généraliser
>
> **Réponse : B.** On fournit des paires (features, label) et l'algorithme apprend la fonction qui les relie. Sans labels, on parle d'apprentissage **non supervisé** (clustering, par exemple).

> [!source] Source primaire
> [Google Machine Learning Crash Course](https://developers.google.com/machine-learning/crash-course), module *ML Models* et introduction. Gratuit, par Google, et aligné sur l'examen.

> [!prof] Une question ?
> Quelque chose n'est pas clair, ou le code plante ? Demande à ton agent-prof. Colle l'erreur telle quelle, c'est son rôle.

**Liens** : [[00 Accueil]] · [[GLOSSAIRE]] · [[Antisèche pandas NumPy scikit-learn]] · suivante : [[0002-train-validation-test|Leçon 0002 : train / validation / test]]
