Retour : [[00 Accueil]] · [[Examen PMLE - vue d'ensemble]]

# Quiz d'entraînement PMLE (15 questions mélangées)

> [!tip] Mode d'emploi
> Les domaines sont **mélangés exprès** (*interleaving*) : à l'examen, tu ne sais pas de quel domaine vient une question. Réponds de mémoire **avant** d'ouvrir la réponse. Note ton score et la date en bas, et refais le quiz dans 1 semaine, puis dans 3 semaines.

> [!quiz]- 1. Des données clients sont dans BigQuery. Le marketing, qui ne connaît que SQL, veut segmenter les clients en groupes homogènes. Que proposer ?
> A) Un modèle KMEANS entraîné directement dans BigQuery ML en SQL
> B) Un réseau de neurones personnalisé entraîné sur des TPU en Python
> C) L'API Natural Language appliquée aux noms et prénoms des clients
> D) Un modèle AutoML Image entraîné sur les photos de profil des clients
>
> **Réponse : A.** C'est du clustering sur des données déjà dans BigQuery, avec une équipe SQL. → [[Domaine 1 Solutions IA low-code]]

> [!quiz]- 2. Un modèle donne 99 % d'accuracy pour détecter une fraude qui ne concerne que 1 % des transactions. Qu'en conclure ?
> A) Le modèle est excellent et peut être déployé dès aujourd'hui
> B) L'accuracy est trompeuse ici, il faut regarder rappel et PR-AUC
> C) Il faut augmenter le nombre d'époques pour atteindre 100 %
> D) Le jeu de test est trop grand et doit être réduit de moitié
>
> **Réponse : B.** Un modèle qui prédit toujours « pas fraude » atteint 99 %. Sur des classes déséquilibrées, on regarde le rappel, la précision et la PR-AUC. → [[Antisèche métriques]]

> [!quiz]- 3. En production, la feature « âge » arrive en mois alors qu'elle était en années à l'entraînement. Comment s'appelle ce problème ?
> A) Concept drift
> B) Data leakage
> C) Training-serving skew
> D) Underfitting
>
> **Réponse : C.** La feature est calculée différemment entre l'entraînement et le serving. → [[Domaine 6 Monitorer les solutions IA]]

> [!quiz]- 4. Il faut scorer 100 millions de lignes chaque dimanche, sans contrainte de latence, au coût le plus bas. Que choisir ?
> A) Un endpoint en ligne toujours actif avec autoscaling configuré
> B) Une prédiction par lots planifiée, avec sortie dans BigQuery
> C) Une boucle Python qui appelle l'endpoint ligne par ligne
> D) Un cluster GKE avec GPU allumé toute la semaine pour ce job
>
> **Réponse : B.** → [[Domaine 4 Servir et scaler]]

> [!quiz]- 5. Une entreprise veut automatiser entraînement, évaluation et déploiement conditionnel, sans gérer d'infrastructure. Quel service ?
> A) Cloud Composer sur un environnement dédié géré par l'équipe
> B) Un cron sur une VM Compute Engine qui lance des scripts Python
> C) Agent Platform Pipelines avec un pipeline Kubeflow (KFP)
> D) Un notebook Workbench relancé chaque matin par un ingénieur
>
> **Réponse : C.** Serverless et conçu pour le ML. → [[Domaine 5 Automatiser les pipelines]]

> [!quiz]- 6. Pour prévoir des ventes, un data scientist mélange aléatoirement les données de 2020 à 2025 avant de les séparer en train et test. Quel est le problème ?
> A) Aucun problème, le mélange aléatoire est toujours la bonne pratique
> B) Le test est trop petit, il faudrait prendre 50 % des données
> C) Le modèle va sous-apprendre faute d'avoir assez de variables
> D) Fuite temporelle : il faut séparer chronologiquement les données
>
> **Réponse : D.** En séries temporelles, le futur ne doit pas servir à prédire le passé. → [[Pièges classiques du ML]]

> [!quiz]- 7. Une équipe a besoin d'une dépendance système spécifique pour entraîner son modèle PyTorch sur l'Agent Platform. Que faire ?
> A) Construire un conteneur personnalisé poussé dans Artifact Registry
> B) Utiliser AutoML tabulaire et ignorer complètement le code PyTorch
> C) Copier la dépendance dans un bucket et espérer qu'elle soit chargée
> D) Entraîner localement puis téléverser seulement les prédictions finales
>
> **Réponse : A.** → [[Domaine 3 Passer du prototype au modèle]]

> [!quiz]- 8. Des données contiennent des numéros de sécurité sociale et doivent servir à l'entraînement. Comment les protéger à grande échelle ?
> A) Les remplacer à la main dans un tableur avant chaque export
> B) Utiliser Sensitive Data Protection pour les détecter et les masquer
> C) Partager le dataset uniquement par e-mail avec l'équipe ML
> D) Les laisser telles quelles, puisque le bucket est déjà privé
>
> **Réponse : B.** → [[Domaine 2 Collaborer données et modèles]]

> [!quiz]- 9. Un assistant basé sur Gemini doit répondre à partir de la documentation produit, mise à jour chaque semaine. Quelle approche ?
> A) Fine-tuner le modèle chaque semaine sur toute la documentation
> B) Du RAG avec un index vectoriel des documents, mis à jour chaque semaine
> C) Écrire toutes les réponses possibles à la main dans le prompt système
> D) Entraîner un modèle de zéro sur la documentation produit
>
> **Réponse : B.** Le RAG garde les réponses à jour sans réentraîner le modèle. → [[M10 IA générative et agents]]

> [!quiz]- 10. La loss d'entraînement et la loss de validation restent toutes deux élevées et plates. Quel diagnostic ?
> A) Sur-apprentissage, donc ajouter du dropout et de la régularisation
> B) Fuite de données entre les jeux d'entraînement et de validation
> C) Sous-apprentissage, donc un modèle plus riche ou de meilleures features
> D) Le modèle est parfait et peut être déployé en production directement
>
> **Réponse : C.** Le modèle n'arrive même pas à apprendre les données d'entraînement. → [[0002-train-validation-test|Leçon 0002]]

> [!quiz]- 11. Un modèle doit être ré-entraîné automatiquement dès qu'une dérive importante est détectée. Quelle architecture ?
> A) Une alerte Model Monitoring qui déclenche le pipeline de ré-entraînement
> B) Un ingénieur qui lit les métriques chaque matin et relance un notebook
> C) Un ré-entraînement toutes les heures, quelle que soit la situation
> D) Un endpoint avec plus de répliques pour compenser la baisse de qualité
>
> **Réponse : A.** On relie le Domaine 6 (alerte) et le Domaine 5 (pipeline), par exemple via Pub/Sub. → [[M9 Monitoring et IA responsable]]

> [!quiz]- 12. Un très gros modèle TensorFlow, dominé par les multiplications matricielles, doit s'entraîner plus vite avec de gros batchs. Quel matériel privilégier ?
> A) Des CPU haute mémoire
> B) Des TPU avec TPUStrategy
> C) Une seule petite VM partagée
> D) Un GPU d'entrée de gamme seul
>
> **Réponse : B.** Les TPU excellent sur les grosses multiplications matricielles avec TF ou JAX. → [[Domaine 3 Passer du prototype au modèle]]

> [!quiz]- 13. Une startup veut classer des avis clients par sentiment (positif ou négatif) dès demain, sans données étiquetées. Que choisir ?
> A) AutoML Text, après avoir étiqueté 10 000 avis à la main
> B) Un Transformer entraîné de zéro sur des TPU pendant un mois
> C) L'API Natural Language pré-entraînée pour l'analyse de sentiment
> D) Un modèle KMEANS dans BigQuery ML sur la longueur des avis
>
> **Réponse : C.** Le cas est générique, il n'y a pas d'étiquettes et le délai est très court : API pré-entraînée. (Un modèle Gemini avec un prompt est aussi acceptable.) → [[Domaine 1 Solutions IA low-code]]

> [!quiz]- 14. On veut déployer une nouvelle version de modèle progressivement, en pouvant revenir en arrière immédiatement. Quelle méthode ?
> A) Supprimer l'ancien endpoint et en créer un nouveau directement
> B) Un split de trafic sur le même endpoint, puis augmenter peu à peu
> C) Prévenir les clients par e-mail du changement de modèle prévu
> D) Tester la nouvelle version sur les données d'entraînement uniquement
>
> **Réponse : B.** C'est un déploiement canary. → [[Domaine 4 Servir et scaler]]

> [!quiz]- 15. Un auditeur demande quel dataset et quel code ont produit le modèle en production il y a 3 mois. Où trouver la réponse ?
> A) Dans la mémoire de l'ingénieur qui a lancé l'entraînement à l'époque
> B) Dans ML Metadata et le lineage des artefacts du pipeline et du Registry
> C) Dans les logs de facturation de Google Cloud du mois concerné
> D) Dans les métriques de latence de l'endpoint de prédiction en ligne
>
> **Réponse : B.** La traçabilité est enregistrée par les pipelines dans ML Metadata, et les versions dans le Model Registry. → [[Domaine 5 Automatiser les pipelines]]

## Mon suivi
| Date | Score /15 | Domaines ratés |
|---|---|---|
| | | |

> [!prof] Une question ?
> Colle tes erreurs à ton agent-prof : il te générera des questions ciblées sur tes points faibles.
