Retour : [[00 Accueil]] · [[Examen PMLE - vue d'ensemble]]

# Domaine 3 : passer du prototype au modèle ML (≈ 21 %, le plus gros domaine)
*Scaling prototypes into ML models*

Module : [[M6 Entraîner à l'échelle]] · Fondations : [[M2 ML classique]], [[M3 Deep learning]] · Leçons : [[0001-entrainer-son-premier-modele|0001]], [[0003-metriques-de-classification|0003]]

> [!warning] Sous-sections reconstituées
> Plan du guide v3, adapté aux nouveaux noms. À vérifier dans le [PDF officiel](https://services.google.com/fh/files/misc/professional_machine_learning_engineer_exam_guide_english_new.pdf).

## 3.1 Construire des modèles
- Choisir le framework : TensorFlow/Keras, PyTorch, scikit-learn, XGBoost, JAX.
- Choisir l'architecture selon le problème (tabulaire, image, texte, séries temporelles).
- **Interprétabilité** : un modèle plus simple vaut parfois mieux qu'un modèle opaque.
- *Transfer learning* et *fine-tuning* de modèles de Model Garden.

## 3.2 Entraîner des modèles
- **Custom training** de l'Agent Platform : conteneurs pré-construits (*prebuilt containers*) ou conteneurs personnalisés (*custom containers*), Artifact Registry.
- Organiser les données d'entraînement : Cloud Storage, BigQuery, TFRecord, `tf.data`.
- **Entraînement distribué** : stratégies TensorFlow (`MirroredStrategy`, `MultiWorkerMirroredStrategy`, `TPUStrategy`), *Reduction Server*, PyTorch DDP.
- **Réglage des hyperparamètres** (*hyperparameter tuning*), avec optimisation bayésienne.
- Diagnostiquer : sur-apprentissage, sous-apprentissage, gradient qui explose ou disparaît, valeurs NaN.
- Fine-tuning de modèles de fondation (supervised tuning, LoRA).

## 3.3 Choisir le matériel
| Situation | Matériel |
|---|---|
| Petit modèle, scikit-learn, XGBoost | CPU |
| Deep learning, opérations personnalisées, PyTorch | GPU (NVIDIA L4, A100, H100…) |
| Grosses multiplications matricielles, TensorFlow/JAX, gros batchs, entraînement long | **TPU** |
| Inférence en périphérie (*edge*) | Modèles compacts : TF Lite, quantification |

## Quiz
> [!quiz]- Q1. Un modèle TensorFlow met 3 jours à s'entraîner sur un seul GPU. L'équipe veut réduire ce temps sans changer l'architecture. Quelle approche ?
> A) Réduire la taille du dataset de moitié pour entraîner plus vite
> B) Passer en CPU haute mémoire pour éviter les limites de la carte GPU
> C) Utiliser MirroredStrategy sur une machine avec plusieurs GPU
> D) Convertir le modèle en BigQuery ML et l'entraîner en SQL
>
> **Réponse : C.** Le parallélisme de données sur plusieurs GPU accélère l'entraînement à architecture égale. A dégrade le modèle.

> [!quiz]- Q2. La loss d'entraînement baisse, mais la loss de validation remonte après l'époque 5. Que faire en premier ?
> A) Augmenter le nombre d'époques pour que la validation finisse par baisser
> B) Ajouter de la régularisation (dropout, L2) et de l'early stopping
> C) Retirer le jeu de validation pour ne garder que l'entraînement
> D) Augmenter fortement le learning rate pour sortir du minimum local
>
> **Réponse : B.** C'est du sur-apprentissage (*overfitting*). On régularise et on arrête tôt. Voir [[Pièges classiques du ML]].

> [!quiz]- Q3. Le code d'entraînement utilise une bibliothèque système C++ absente des conteneurs Google. Comment l'entraîner sur l'Agent Platform ?
> A) Construire un custom container, le pousser dans Artifact Registry, lancer un custom job
> B) Utiliser AutoML tabulaire en lui passant le code source en paramètre d'entrée
> C) Installer la bibliothèque à la main dans un notebook Workbench à chaque fois
> D) Réécrire tout le modèle en SQL pour pouvoir l'entraîner dans BigQuery ML
>
> **Réponse : A.** Les dépendances non standard imposent un conteneur personnalisé. C n'est pas reproductible.

> [!quiz]- Q4. Une équipe veut trouver le meilleur learning rate et la meilleure profondeur parmi beaucoup de combinaisons, en limitant le nombre d'essais coûteux. Que faire ?
> A) Une recherche en grille exhaustive lancée à la main sur une seule VM
> B) Le hyperparameter tuning managé, avec optimisation bayésienne
> C) Choisir les valeurs par défaut du framework et ne plus y toucher
> D) Tester une valeur par jour et noter les résultats dans un tableur
>
> **Réponse : B.** Le tuning managé explore intelligemment l'espace des hyperparamètres et parallélise les essais.

## Ce qu'il faut retenir
- [ ] Conteneur pré-construit ou personnalisé : je sais choisir
- [ ] Je connais les stratégies distribuées TF et quand utiliser un TPU
- [ ] Je sais diagnostiquer le sur-apprentissage et le sous-apprentissage avec les courbes de loss
- [ ] Je connais le hyperparameter tuning managé et ses algorithmes (grille, aléatoire, bayésien)
- [ ] Je sais quand choisir CPU, GPU ou TPU

> [!source] Source primaire
> [[CS230]] (pratique du deep learning) et la doc *custom training* de l'Agent Platform, via le [learning path](https://www.cloudskillsboost.google/paths/17).

> [!prof] Une question ?
> Demande à ton agent un exercice de diagnostic de courbes de loss.
