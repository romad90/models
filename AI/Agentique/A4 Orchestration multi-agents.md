# A4 Orchestration multi-agents

Retour : [[Piste Agentique]] · Précédent : [[A5 Agents en production sur Google Cloud]] · Suivant : [[A7 Fine-tuning et RL pour agents]]
Semaines : **S18–S20** (en même temps que [[M8 Pipelines et MLOps]])

> [!examen] Pourquoi
> Le multi-agents est à la mode, et souvent mal utilisé. Savoir **quand ne pas** l'utiliser est un signal de séniorité.

## Diagnostic express
> [!quiz]- Dans quel cas une architecture multi-agents se justifie-t-elle le mieux ?
> A) Recherche large, parallélisable, qui dépasse un seul contexte
> B) Tâche séquentielle courte, avec étapes fortement dépendantes
> C) Petite application où le budget de tokens est très serré
> D) Modification de code qui touche un seul fichier source
>
> **Réponse : A.** Les sous-agents isolent leur contexte et travaillent en parallèle, ce qui est utile pour l'exploration large. Le prix : beaucoup plus de tokens et une coordination difficile. B, C et D sont mieux servis par un seul agent.

## Notions
- **Motifs de workflows** : chaîne de prompts, routage, parallélisation, orchestrateur et exécutants, évaluateur et optimiseur
- **Orchestrateur et sous-agents** : délégation claire (objectif, format de sortie, limites), synthèse condensée en retour, budget d'effort selon la difficulté
- **Coûts cachés** : multiplication des tokens, erreurs qui se propagent, non-déterminisme, débogage difficile ; il faut des traces de bout en bout
- **Coordination** : état partagé ou messages, A2A entre agents de fournisseurs différents, reprise après erreur (*checkpoints*)
- **Parallèle avec le MLOps** : un graphe d'agents ressemble à un pipeline, avec composants, artefacts et lignage, voir [[Domaine 5 Automatiser les pipelines]]

## À toi
> [!exercice] Un contre plusieurs
> 1. Choisis une tâche de recherche réelle de ton travail.
> 2. Implémente une version mono-agent et une version orchestrateur + 3 sous-agents parallèles.
> 3. Compare qualité (ton éval), coût en tokens et latence. Conclus quand le multi-agents vaut son prix.

> [!source] Sources primaires
> - Anthropic, [Building effective agents](https://www.anthropic.com/engineering/building-effective-agents) (motifs de workflows)
> - Anthropic Engineering : billet sur leur système de recherche multi-agents, à lire sur le [blog Engineering](https://www.anthropic.com/engineering) (lien exact à vérifier)

> [!prof] Une question ?
> Décris ton architecture actuelle à ton agent-prof et demande-lui ce qu'il simplifierait.
