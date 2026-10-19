Retour : [[00 Accueil]] · [[Examen PMLE - vue d'ensemble]]

# Domaine 6 : monitorer les solutions IA (≈ 13 %)
*Monitoring AI solutions*

Module : [[M9 Monitoring et IA responsable]]

> [!warning] Sous-sections reconstituées
> Plan du guide v3, adapté aux nouveaux noms. À vérifier dans le [PDF officiel](https://services.google.com/fh/files/misc/professional_machine_learning_engineer_exam_guide_english_new.pdf).

## 6.1 Identifier les risques des solutions IA
- **Sécurité** : IAM et moindre privilège, comptes de service, VPC Service Controls, chiffrement CMEK, protection contre l'injection de prompt (*prompt injection*) et l'exfiltration de données.
- **IA responsable** : biais et équité (*fairness*), principes d'IA de Google, documentation (*model cards*), filtres de sécurité des modèles génératifs.
- **Explicabilité** : Explainable AI (attributions de features : Sampled Shapley, Integrated Gradients, XRAI), `ML.EXPLAIN_PREDICT` dans BigQuery ML.

## 6.2 Monitorer, tester et dépanner
- **Model Monitoring** de l'Agent Platform :
  - **Training-serving skew** : la distribution des features en production diffère de celle de l'entraînement.
  - **Dérive des prédictions ou des features** (*prediction / feature drift*) : la distribution en production change avec le temps.
  - Seuils, alertes, fenêtre d'échantillonnage, puis déclenchement du ré-entraînement ([[Domaine 5 Automatiser les pipelines]]).
- *Concept drift* : la relation entre X et y change (par exemple, le comportement des clients après une crise).
- Monitoring des performances : latence, erreurs, utilisation des ressources (Cloud Monitoring, Cloud Logging).
- Évaluer les modèles génératifs : qualité, toxicité, ancrage (*groundedness*), évaluation automatique.

## Skew ou drift ?
| | Compare | Exemple |
|---|---|---|
| Training-serving skew | Entraînement et production | Une feature calculée différemment en ligne |
| Drift | Production à t et production à t+1 | Les âges des clients changent avec le temps |
| Concept drift | La relation entre X et y | Une fraude d'un nouveau type apparaît |

## Quiz
> [!quiz]- Q1. Un modèle de détection de fraude perd en précision six mois après son déploiement. Les fraudeurs ont changé de technique. De quoi s'agit-il ?
> A) D'un training-serving skew dû à un bug dans le code de prétraitement
> B) D'un sur-apprentissage qui apparaît seulement après quelques mois
> C) D'un concept drift, puisque la relation entre features et cible a changé
> D) D'une fuite de données (data leakage) entre le train et le jeu de test
>
> **Réponse : C.** Le lien entre les entrées et la cible a évolué : c'est un *concept drift*. Il faut détecter la baisse et ré-entraîner sur des données récentes.

> [!quiz]- Q2. Un régulateur exige qu'une banque explique pourquoi chaque demande de crédit a été refusée. Que mettre en place ?
> A) Remplacer le modèle par un tirage au sort pour garantir l'équité
> B) Activer Explainable AI pour obtenir les attributions par prédiction
> C) Augmenter la taille du modèle pour améliorer la précision globale
> D) Supprimer le logging pour ne pas conserver de trace des décisions
>
> **Réponse : B.** Les attributions de features (par exemple Sampled Shapley) expliquent chaque prédiction individuelle.

> [!quiz]- Q3. L'équipe veut être alertée automatiquement quand la distribution d'une feature en production s'écarte de celle de l'entraînement. Que faire ?
> A) Configurer Model Monitoring pour la détection de skew, avec un seuil d'alerte
> B) Relire à la main un échantillon des requêtes chaque trimestre
> C) Ré-entraîner le modèle chaque jour sans aucune analyse des données
> D) Augmenter le nombre de répliques de l'endpoint pour absorber l'écart
>
> **Réponse : A.** Model Monitoring compare les distributions automatiquement et alerte au-delà d'un seuil.

> [!quiz]- Q4. Un modèle de recrutement favorise systématiquement un groupe démographique. Quelle première étape ?
> A) Cacher les résultats du modèle aux personnes concernées par la décision
> B) Évaluer les métriques par sous-groupe pour mesurer le biais
> C) Retirer le jeu de validation, qui fait apparaître le problème
> D) Augmenter le learning rate pour que le modèle apprenne plus vite
>
> **Réponse : B.** On mesure d'abord l'équité par segment (*sliced evaluation*), puis on corrige (données, re-pondération, contraintes).

## Ce qu'il faut retenir
- [ ] Je sais distinguer skew, drift et concept drift
- [ ] Je sais configurer Model Monitoring et relier ses alertes au ré-entraînement
- [ ] Je connais les méthodes d'Explainable AI et quand les utiliser
- [ ] Je connais les bases de l'IA responsable : biais, évaluation par segment, model cards
- [ ] Je connais la sécurité des solutions IA : IAM, VPC-SC, CMEK, injection de prompt

> [!source] Source primaire
> [Google : Responsible AI practices](https://ai.google/responsibility/responsible-ai-practices/) et la doc *Model Monitoring* de l'Agent Platform.

> [!prof] Une question ?
> Demande à ton agent : « quel monitoring pour mon [[Projet fil rouge]] ? ».
