---
semaines: S10–S13
domaine_examen: "[[Domaine 3 Passer du prototype au modèle]]"
---
# M3 Deep learning

Retour : [[00 Accueil]] · Précédent : [[M2 ML classique]] · Suivant : [[M4 Google Cloud et Agent Platform]]

> [!examen] Pourquoi
> L'examen suppose que tu sais quand choisir un réseau de neurones, comment l'entraîner (TensorFlow/Keras, PyTorch) et comment régler les problèmes classiques : gradients qui explosent, sur-apprentissage, choix de l'optimiseur.

## Semaine par semaine
| Sem. | Thème | Source |
|---|---|---|
| S10 | Neurone, couches, fonctions d'activation, rétropropagation | [[CS230]] ; 3Blue1Brown, *Neural networks* |
| S11 | Keras (`Sequential`, `compile`, `fit`) et boucle PyTorch ; *dropout*, *batch norm*, *early stopping* | [Tutoriels TensorFlow](https://www.tensorflow.org/tutorials), [Tutoriels PyTorch](https://pytorch.org/tutorials/) |
| S12 | CNN, augmentation de données, *transfer learning* | [[CS231N]] (notes en ligne) |
| S13 | Embeddings, RNN, attention, Transformers | [[CS224N]] cours 1–2 et cours sur les Transformers |

## Compétences visées
- [ ] Entraîner un réseau dense sur des données tabulaires avec Keras
- [ ] Faire du *transfer learning* sur un petit jeu d'images
- [ ] Expliquer ce qu'est un embedding et pourquoi l'attention a remplacé les RNN
- [ ] Savoir quand un GPU ou un TPU est utile (cela prépare [[M6 Entraîner à l'échelle]])

> [!source] Source primaire
> [[CS230]] (cours en vidéo) et le livre de Géron, *Hands-On ML*, chap. 10–16.

> [!prof] Une question ?
> Demande à ton agent de t'expliquer la rétropropagation sur un réseau à 2 neurones, avec des chiffres.
