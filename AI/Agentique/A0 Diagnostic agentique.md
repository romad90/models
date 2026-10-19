# A0 Diagnostic agentique

Retour : [[Piste Agentique]] · Suivant : [[A2 Context engineering et outils]]

> [!examen] Pourquoi
> Le skill `teach` exige d'enseigner dans ta **zone proximale de développement**. Ce diagnostic dit à ton agent-prof quoi sauter et où insister.

## Mode d'emploi
Réponds **par écrit, sans chercher**, en 3 à 5 lignes par question. Puis colle tes réponses à ton agent-prof avec : « corrige mon diagnostic A0 et écris les learning records ».

## Questions
1. **Évals** : comment sais-tu aujourd'hui qu'un changement de prompt a amélioré ton agent en production ? Quelles métriques suis-tu ?
2. **Contexte** : ton agent fait une tâche longue (plus de 50 appels d'outils). Comment empêches-tu le contexte de se dégrader ?
3. **Outils** : quelles règles suis-tu pour concevoir un outil (nom, description, format de retour, erreurs) ?
4. **Architecture** : quand choisis-tu un *workflow* (chaîne, routage, parallélisation) plutôt qu'un agent autonome ? Et quand plusieurs agents ?
5. **Sécurité** : ton agent lit des pages web ou des emails. Décris une attaque par injection indirecte de prompt et trois défenses.
6. **Coûts et latence** : cite trois leviers pour diviser par deux le coût d'un agent sans perdre en qualité.
7. **Sous le capot** : qu'est-ce qu'un token, et pourquoi la température 0 ne garantit-elle pas un résultat déterministe ?
8. **Entraînement** : quelle différence entre *SFT*, RLHF/DPO et RL avec récompense vérifiable ? Quand un *fine-tuning* vaut-il mieux qu'un meilleur prompt ?
9. **Production** : comment gères-tu les versions de prompts et de modèles, et le retour arrière ?
10. **Observabilité** : que contient une bonne trace d'agent ?

## Grille (pour l'agent-prof)
| Question | Module si la réponse est faible |
|---|---|
| 1, 10 | [[A3 Évaluer les agents]] |
| 2, 3 | [[A2 Context engineering et outils]] |
| 4 | [[A4 Orchestration multi-agents]] |
| 5 | [[A6 Sécurité des agents]] |
| 6, 9 | [[A5 Agents en production sur Google Cloud]] |
| 7 | [[A1 Sous le capot des LLM]] |
| 8 | [[A7 Fine-tuning et RL pour agents]] |

> [!prof] Une question ?
> Ce diagnostic n'est pas noté : il sert à ne pas te faire perdre de temps.
