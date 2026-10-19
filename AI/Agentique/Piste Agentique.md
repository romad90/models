# 🤖 Piste Agentique (niveau avancé)

Retour : [[00 Accueil]] · Mission : [[MISSION]] · Plan : [[Plan 26 semaines]]

> [!examen] Pourquoi
> Tu construis déjà des agents. Cette piste vise ce qui sépare un bon praticien d'un **AI Engineer senior** : **mesurer** au lieu de deviner, concevoir le contexte comme une ressource rare, sécuriser, maîtriser les coûts et comprendre le modèle sous le capot.

## Organisation
Environ **3 h/semaine** en parallèle de la piste ML/PMLE. Chaque module commence par un **diagnostic** : si tu réponds juste sans hésiter, passe directement à l'exercice de niveau supérieur.

| Module | Semaines | Lien avec la piste ML |
|---|---|---|
| [[A0 Diagnostic agentique]] | S1 | – |
| [[A2 Context engineering et outils]] | S2–S4 | – |
| [[A3 Évaluer les agents]] | S5–S8 | [[0003-metriques-de-classification\|Leçon 3]] (métriques), [[M2 ML classique]] |
| [[A6 Sécurité des agents]] | S9–S10 | [[M9 Monitoring et IA responsable]] |
| [[A1 Sous le capot des LLM]] | S11–S13 | [[M3 Deep learning]], [[CS224N]] |
| [[A5 Agents en production sur Google Cloud]] | S14–S17 | [[M4 Google Cloud et Agent Platform]], [[M7 Servir les modèles]] |
| [[A4 Orchestration multi-agents]] | S18–S20 | [[M8 Pipelines et MLOps]] |
| [[A7 Fine-tuning et RL pour agents]] | S21–S23 | [[M6 Entraîner à l'échelle]], [[CS336]], [[CS329A]] |
| Synthèse et projet | S24 | [[M10 IA générative et agents]], [[Projet fil rouge]] |

## Principes transverses
1. **Éval d'abord** : aucune modification de prompt, d'outil ou de modèle sans jeu d'évaluation.
2. **Le contexte est un budget** : chaque token doit apporter du signal.
3. **Le plus simple qui marche** : un *workflow* déterministe bat un agent autonome quand la tâche est prévisible.
4. **Observabilité** : traces, coûts et latence par étape, sinon on ne peut ni déboguer ni optimiser.

> [!source] Sources primaires de la piste
> - Anthropic, [Building effective agents](https://www.anthropic.com/engineering/building-effective-agents)
> - Anthropic, [Effective context engineering for AI agents](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents)
> - [Stanford CS329A : Self-Improving AI Agents](https://cs329a.stanford.edu/) (automne 2025), voir [[CS329A]]
> - [Berkeley RDI : Agentic AI MOOC](https://rdi.berkeley.edu/education) (gratuit)
