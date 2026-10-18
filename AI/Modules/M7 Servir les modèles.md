---
semaines: S21
domaine_examen: "[[Domaine 4 Servir et scaler]]"
---
# M7 Servir les modèles

Retour : [[00 Accueil]] · Précédent : [[M6 Entraîner à l'échelle]] · Suivant : [[M8 Pipelines et MLOps]]

> [!examen] Pourquoi
> Le domaine 4 (environ 20 %) porte sur la mise à disposition des prédictions : en ligne ou par lots, avec la bonne latence, le bon coût et sans interruption de service.

## Thèmes
- Prédiction **en ligne** (endpoints) ou **par lots** (*batch prediction*) : quand choisir quoi
- Mise à l'échelle automatique, choix des machines et des accélérateurs
- Déploiement progressif : partage du trafic, A/B testing, *canary*, retour arrière
- Alternatives : Cloud Run, GKE, BigQuery ML `ML.PREDICT`
- Optimisation de l'inférence : quantification, distillation, mise en cache

## Compétences visées
- [ ] Déployer un modèle du Model Registry vers un endpoint et l'appeler
- [ ] Lancer une prédiction par lots sur un fichier de Cloud Storage
- [ ] Répartir le trafic 90/10 entre deux versions d'un modèle
- [ ] Choisir entre endpoint, Cloud Run et batch à partir d'un énoncé (latence, volume, coût)

> [!source] Source primaire
> La documentation « Get predictions » d'Agent Platform, et *Designing ML Systems*, chap. 7 ([[CS329S]]).

> [!prof] Une question ?
> Demande à ton agent : « mon endpoint coûte trop cher, quelles options ? »
