Retour : [[00 Accueil]] · [[Examen PMLE - vue d'ensemble]]

# Domaine 4 : servir et passer à l'échelle (≈ 20 %)
*Serving and scaling models*

Module : [[M7 Servir les modèles]]

> [!warning] Sous-sections reconstituées
> Plan du guide v3, adapté aux nouveaux noms. À vérifier dans le [PDF officiel](https://services.google.com/fh/files/misc/professional_machine_learning_engineer_exam_guide_english_new.pdf).

## 4.1 Servir les modèles
- **Prédiction en ligne** (*online prediction*) : un endpoint de l'Agent Platform (ex-Vertex AI Endpoints), pour une faible latence, une requête à la fois.
- **Prédiction par lots** (*batch prediction*) : de gros volumes, pas de contrainte de latence, résultats dans BigQuery ou Cloud Storage. Alternative : `ML.PREDICT` dans BigQuery ML.
- Conteneurs de serving pré-construits ou personnalisés (TF Serving, TorchServe, vLLM pour les LLM).
- Autres cibles : GKE, Cloud Run, edge (TF Lite).
- **Model Registry** : versions, alias, déploiement d'une version précise.
- Tests en production : **split de trafic** (*traffic splitting*), canary, A/B testing.
- Servir des features en ligne (Feature Store, faible latence).

## 4.2 Passer le serving à l'échelle
- **Autoscaling** : nombre minimal et maximal de répliques, choix du type de machine, GPU pour l'inférence.
- Optimiser la latence : quantification, distillation, mise en cache, batching, modèle plus petit.
- Plusieurs modèles sur un même endpoint, ressources partagées.
- Servir des LLM : débit en tokens, coût, choix entre API managée (Gemini) et modèle auto-hébergé.

## Online ou batch ?
| Besoin | Choix |
|---|---|
| Réponse en moins de 100 ms à un utilisateur | Endpoint en ligne |
| Scorer 50 millions de clients chaque nuit | Prédiction par lots |
| Données déjà dans BigQuery, scoring SQL | `ML.PREDICT` |
| Pas de réseau (appareil mobile) | Edge : TF Lite |

## Quiz
> [!quiz]- Q1. Une app doit recommander des produits pendant que l'utilisateur navigue, en moins de 100 ms. Quelle solution ?
> A) Une prédiction par lots chaque nuit, stockée dans un fichier CSV
> B) Un endpoint en ligne avec autoscaling et features servies en ligne
> C) Un notebook Workbench qui calcule les scores quand on le relance
> D) Une requête BigQuery ML lancée à chaque clic sur le site de vente
>
> **Réponse : B.** La faible latence et le temps réel imposent un endpoint en ligne. A n'est pas personnalisé à la session.

> [!quiz]- Q2. Une banque calcule un score de risque pour 30 millions de comptes une fois par mois. Il n'y a pas de besoin de temps réel et le coût doit être minimal. Que choisir ?
> A) Un endpoint en ligne avec 50 répliques actives en permanence
> B) Un cluster GKE dédié qui tourne toute l'année pour ce calcul
> C) Un job de prédiction par lots, lancé chaque mois, sans endpoint
> D) Une fonction Cloud Run appelée une fois par compte, à la chaîne
>
> **Réponse : C.** Le batch est fait pour ce cas. Pas de ressources qui tournent entre deux exécutions, donc coût minimal.

> [!quiz]- Q3. Une équipe veut tester une nouvelle version de modèle sur 10 % du trafic réel avant de la généraliser. Que faire ?
> A) Remplacer l'ancien modèle par le nouveau directement, sans aucun test
> B) Déployer les deux versions sur l'endpoint avec un split de trafic 90/10
> C) Créer un second site web pour faire le test avec les nouveaux clients
> D) Évaluer le nouveau modèle uniquement sur le jeu de test historique
>
> **Réponse : B.** Le split de trafic sur un même endpoint permet un déploiement canary et un retour arrière facile.

> [!quiz]- Q4. La latence d'un modèle de deep learning est trop élevée sur CPU, et le budget GPU est limité. Quelle optimisation essayer d'abord ?
> A) Quantifier le modèle (par exemple en INT8) pour réduire le coût de calcul
> B) Ajouter des couches au réseau pour améliorer la précision des prédictions
> C) Réentraîner le modèle sur un dataset dix fois plus grand qu'avant
> D) Passer en prédiction par lots, même si le besoin est en temps réel
>
> **Réponse : A.** La quantification réduit la taille et la latence avec une perte de précision souvent faible. D contredit le besoin.

## Ce qu'il faut retenir
- [ ] Prédiction en ligne ou par lots : je sais choisir en une seconde
- [ ] Je sais configurer l'autoscaling (nombre minimal et maximal de répliques) et choisir la machine
- [ ] Je sais faire un canary ou un A/B test par split de trafic
- [ ] Je connais les leviers de latence : quantification, distillation, batching, cache
- [ ] Je sais quand servir hors Agent Platform (GKE, Cloud Run, edge)

> [!source] Source primaire
> [[CS329S]] (ML systems design, partie déploiement) et la doc *prediction* de l'Agent Platform.

> [!prof] Une question ?
> Demande à ton agent de concevoir le serving de ton [[Projet fil rouge]] avec toi.
