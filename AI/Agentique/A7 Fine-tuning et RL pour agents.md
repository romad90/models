# A7 Fine-tuning et RL pour agents

Retour : [[Piste Agentique]] · Précédent : [[A4 Orchestration multi-agents]]
Semaines : **S21–S23** (après [[M6 Entraîner à l'échelle]])

> [!examen] Pourquoi
> C'est là que tes nouvelles fondations ML rejoignent l'agentique : adapter un modèle à tes tâches, distiller un gros modèle en petit pour réduire les coûts, et comprendre les agents qui s'améliorent eux-mêmes ([[CS329A]]). L'examen PMLE couvre le *tuning* sur Agent Platform.

## Diagnostic express
> [!quiz]- Ton agent formate mal ses appels d'outils malgré un bon prompt. Que tenter ?
> A) Un fine-tuning supervisé sur des trajectoires correctes annotées
> B) Un pré-entraînement complet sur un grand corpus de code
> C) Une augmentation de la fenêtre de contexte du modèle utilisé
> D) Un passage à une température plus élevée pour chaque appel
>
> **Réponse : A.** Un comportement de **forme** stable et répétitif est le cas idéal du SFT. B est hors de portée et inutile, C et D ne traitent pas le problème.

## Notions
- **Choisir le bon outil** : prompt, puis RAG, puis *fine-tuning*, avec un critère de décision écrit
- **SFT** et réglage efficace (**LoRA**, **QLoRA**) ; **distillation** d'un grand modèle vers un petit à partir de tes traces de production
- **Préférences** : RLHF, **DPO**
- **RL avec récompenses vérifiables** : l'éval de [[A3 Évaluer les agents]] devient une fonction de récompense
- **Agents qui s'améliorent** : réflexion, auto-critique, recherche au moment de l'inférence, apprentissage à partir de l'environnement ([[CS329A]])
- **Sur Google Cloud** : *tuning* supervisé de Gemini et modèles ouverts de Model Garden sur Agent Platform

## À toi
> [!exercice] Distiller ton agent
> 1. Extrais 300 à 1 000 trajectoires réussies d'un grand modèle sur une sous-tâche étroite.
> 2. Fais un fine-tuning LoRA d'un petit modèle ouvert (ou un *tuning* supervisé sur Agent Platform).
> 3. Compare avec ton éval : qualité, coût par tâche, latence.
> 4. Rédige la décision dans un *learning record* : est-ce que ça vaut la peine en production ?

> [!source] Sources primaires
> - [[CS329A]] : Self-Improving AI Agents
> - [[CS336]] : cours sur l'alignement et le RL
> - [[CS224N]] : cours sur le post-entraînement

> [!prof] Une question ?
> Demande à ton agent-prof de t'aider à construire ton jeu de données de SFT à partir de tes traces.
