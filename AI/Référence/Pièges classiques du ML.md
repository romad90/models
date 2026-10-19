Retour : [[00 Accueil]] · Leçon : [[0002-train-validation-test|0002 Train / validation / test]]

# Pièges classiques du ML

| Piège | Symptôme | Remède |
|---|---|---|
| **Fuite de données** (*data leakage*) | Score de test irréaliste (par exemple 99 %), qui s'effondre en production | Retirer les features qui « connaissent » la réponse. Faire le `fit` du prétraitement sur le train seulement (Pipeline sklearn ou TFX Transform) |
| **Mauvais split en séries temporelles** | Très bon en test, mauvais en production | Séparer **chronologiquement** : entraîner sur le passé, tester sur le futur (`TimeSeriesSplit`) |
| **Fuite par groupe** | Le même client ou patient se retrouve dans le train et le test | Séparer par groupe (`GroupKFold`) |
| **Sur-apprentissage** (*overfitting*) | Loss d'entraînement ↓, loss de validation ↑ | Plus de données, régularisation (L1/L2, dropout), early stopping, modèle plus simple, augmentation de données |
| **Sous-apprentissage** (*underfitting*) | Losses d'entraînement et de validation hautes | Modèle plus riche, meilleures features, entraîner plus longtemps, moins de régularisation |
| **Classes déséquilibrées** | Accuracy élevée, mais la classe rare n'est jamais trouvée | Métriques adaptées (rappel, PR-AUC), poids de classes, sur- ou sous-échantillonnage, ajuster le seuil |
| **Training-serving skew** | Bon hors ligne, mauvais en ligne | Même code de transformation pour l'entraînement et le serving (Feature Store, TFX Transform), surveiller avec Model Monitoring |
| **Dérive** (*data / concept drift*) | La performance baisse peu à peu après le déploiement | Monitoring, alertes, ré-entraînement automatique ([[Domaine 6 Monitorer les solutions IA]]) |
| **Tester sur le jeu de test plusieurs fois** | On « optimise » sur le test, et le score devient optimiste | Régler sur la validation, toucher au test **une seule fois** à la fin |
| **Features non normalisées** | Descente de gradient lente ou instable, k-NN et SVM biaisés | `StandardScaler` ou `MinMaxScaler` (les arbres n'en ont pas besoin) |
| **Valeurs manquantes mal gérées** | Erreurs, ou biais silencieux | Imputer (médiane, mode), ajouter une feature indicatrice « manquant » |
| **Corrélation prise pour causalité** | Décisions métier erronées | Expériences contrôlées (A/B test), prudence dans l'interprétation |
| **Biais dans les données** | Le modèle est injuste envers un groupe | Évaluation par sous-groupe, données plus représentatives ([[M9 Monitoring et IA responsable]]) |

> [!examen] À l'examen
> Une question qui annonce un score « trop beau » cache presque toujours une **fuite de données**. Une question qui parle de performances qui se dégradent avec le temps cache de la **dérive**.

Liés : [[Antisèche métriques]] · [[Domaine 3 Passer du prototype au modèle]]
