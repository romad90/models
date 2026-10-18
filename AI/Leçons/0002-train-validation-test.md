---
module: "[[M2 ML classique]]"
domaine_examen: "[[Domaine 3 Passer du prototype au modèle]]"
statut: à faire
---
# Leçon 0002 : train / validation / test

> [!examen] Pourquoi c'est important pour la mission
> À l'examen PMLE comme en entretien, beaucoup de scénarios cachent un **mauvais découpage des données** : fuite de données, sur-apprentissage, mélange aléatoire de séries temporelles. Savoir découper, c'est savoir faire confiance à ses chiffres.

## Ce que tu sauras faire à la fin
Diagnostiquer un sur-apprentissage en comparant la performance sur l'entraînement et sur le test.

## L'essentiel (connaissances)

**Trois ensembles, trois rôles** ([Google MLCC : datasets, generalization, and overfitting](https://developers.google.com/machine-learning/crash-course/overfitting)) :

| Ensemble | Rôle | Quand l'utiliser |
|---|---|---|
| **Entraînement** (*training set*) | ajuster les paramètres (`fit`) | tout le temps |
| **Validation** (*validation set*) | choisir les hyperparamètres et comparer les modèles | pendant le développement |
| **Test** (*test set*) | estimer la performance finale | **une seule fois**, à la fin |

Si tu regardes le test pour choisir tes réglages, il devient une deuxième validation et ton estimation finale est trop optimiste.

**Sur- et sous-apprentissage** ([CS229, notes sur le compromis biais/variance](https://cs229.stanford.edu/)) :
- **Sur-apprentissage** (*overfitting*) : excellent sur l'entraînement, nettement moins bon sur le test. Le modèle a mémorisé le bruit.
- **Sous-apprentissage** (*underfitting*) : mauvais partout. Le modèle est trop simple.

**Validation croisée** (*k-fold cross-validation*) : on coupe les données en *k* blocs. Chaque bloc sert tour à tour de validation, et on fait la moyenne des *k* scores. C'est plus fiable quand on a peu de données ([doc scikit-learn](https://scikit-learn.org/stable/modules/cross_validation.html)).

**Séries temporelles** : on ne mélange **jamais** au hasard. On entraîne sur le passé et on teste sur le futur (`TimeSeriesSplit`), sinon le modèle « voit l'avenir ». C'est une forme de **fuite de données** (*data leakage*), voir [[Pièges classiques du ML]].

## À toi (compétence)

> [!exercice] Exercice : provoquer un sur-apprentissage
> Dans Colab :
> ```python
> from sklearn.datasets import load_breast_cancer
> from sklearn.model_selection import train_test_split, cross_val_score
> from sklearn.tree import DecisionTreeClassifier
>
> X, y = load_breast_cancer(return_X_y=True)
> X_train, X_test, y_train, y_test = train_test_split(
>     X, y, test_size=0.2, random_state=42, stratify=y)
>
> for depth in [None, 3]:           # None = arbre sans limite de profondeur
>     tree = DecisionTreeClassifier(max_depth=depth, random_state=42)
>     tree.fit(X_train, y_train)
>     print(f"max_depth={depth}: train={tree.score(X_train, y_train):.3f} "
>           f"test={tree.score(X_test, y_test):.3f}")
>
> # Validation croisée 5 blocs, sur l'entraînement uniquement
> scores = cross_val_score(DecisionTreeClassifier(max_depth=3, random_state=42),
>                          X_train, y_train, cv=5)
> print("CV moyenne :", scores.mean().round(3))
> ```
> **Résultat attendu** : l'arbre sans limite obtient **train = 1,000** et un test sensiblement plus bas (~0,90–0,94). L'arbre de profondeur 3 a un écart train/test beaucoup plus faible.
> **Ta mission** : écris en une phrase lequel des deux sur-apprend, et pourquoi. Puis demande à ton agent-prof de vérifier ta phrase.

## Rappel actif

> [!quiz]- Q1. Accuracy : 100 % en entraînement, 70 % en test. Diagnostic ?
> A) Sous-apprentissage : le modèle est trop simple
> B) Sur-apprentissage : le modèle mémorise le bruit
> C) Fuite de données entre les deux
> D) Bon modèle : cet écart est normal
>
> **Réponse : B.** Un grand écart entre train et test est la signature du sur-apprentissage. Le sous-apprentissage donnerait de mauvais scores **partout**. La fuite de données, elle, gonfle souvent **aussi** le score de test.

> [!quiz]- Q2. À quoi sert l'ensemble de validation ?
> A) Entraîner le modèle sur plus de données
> B) Remplacer l'ensemble de test en production finale
> C) Stocker les données mal étiquetées à part
> D) Choisir les hyperparamètres sans toucher au test
>
> **Réponse : D.** La validation sert à régler et à comparer les modèles. Le test reste intact pour une estimation honnête, faite une seule fois.

> [!quiz]- Q3. Tu prédis les ventes de demain. Comment découper ?
> A) Entraîner sur le passé, tester sur le futur
> B) Mélanger aléatoirement toutes les lignes avant de découper
> C) Ne garder que les données du dernier mois
> D) Tester sur le passé, entraîner sur le futur
>
> **Réponse : A.** Pour les données temporelles, le découpage doit respecter le temps. Mélanger laisserait le modèle s'entraîner sur des jours postérieurs à ceux qu'il est censé prédire : c'est une fuite de données.

> [!quiz]- Q4. En validation croisée à 5 blocs (k = 5) :
> A) On entraîne cinq fois sur toutes les données
> B) On teste cinq modèles sur l'ensemble de test
> C) Chaque bloc sert tour à tour de validation
> D) On garde uniquement le meilleur des cinq blocs
>
> **Réponse : C.** On fait 5 entraînements, chacun valide sur un bloc différent, et on rapporte la **moyenne** des 5 scores. Garder le meilleur bloc serait de la triche optimiste.

> [!source] Source primaire
> [Google MLCC : *Datasets, generalization, and overfitting*](https://developers.google.com/machine-learning/crash-course/overfitting), complété par la [doc scikit-learn sur la validation croisée](https://scikit-learn.org/stable/modules/cross_validation.html).

> [!prof] Une question ?
> Pas sûr de la différence entre paramètre et hyperparamètre ? Demande à ton agent-prof.

**Liens** : [[00 Accueil]] · [[GLOSSAIRE]] · [[Pièges classiques du ML]] · précédente : [[0001-entrainer-son-premier-modele|Leçon 0001]] · suivante : [[0003-metriques-de-classification|Leçon 0003 : métriques de classification]]
