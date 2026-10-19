# A2 Context engineering et outils

Retour : [[Piste Agentique]] · Précédent : [[A0 Diagnostic agentique]] · Suivant : [[A3 Évaluer les agents]]
Semaines : **S2–S4**

> [!examen] Pourquoi
> La plupart des échecs d'agents en production sont des échecs de **contexte** (trop, pas assez, mal ordonné) ou d'**outils** (ambigus, redondants, retours trop verbeux), pas des échecs de modèle.

## Diagnostic express
> [!quiz]- Ton agent a 40 outils et choisit souvent le mauvais. Première action ?
> A) Passer à un modèle plus grand et plus cher
> B) Réduire et fusionner les outils qui se recoupent
> C) Ajouter des exemples few-shot pour chaque outil
> D) Augmenter la température pour explorer davantage
>
> **Réponse : B.** Les outils qui se chevauchent sont un mode d'échec classique : si un humain ne sait pas dire quel outil utiliser, l'agent ne fera pas mieux. C peut aider ensuite, A coûte cher sans traiter la cause, D aggrave les choses.

## Notions (niveau avancé)
- **Le contexte comme budget d'attention** : viser le plus petit ensemble de tokens à fort signal. La qualité se dégrade bien avant la limite de la fenêtre (*context rot*).
- **Quatre leviers** : *écrire* (mémoire externe, fichiers de notes), *sélectionner* (récupération juste à temps plutôt que tout précharger), *compresser* (résumés, compaction, suppression des vieux résultats d'outils), *isoler* (sous-agents avec leur propre contexte, qui ne renvoient qu'une synthèse).
- **Prompt système à la bonne altitude** : ni règles fragiles en `if/else`, ni consignes vagues. Un plan structuré par sections.
- **Conception d'outils** : noms sans ambiguïté, paramètres explicites, retours concis et lisibles par le modèle (identifiants sémantiques plutôt que UUID), pagination et troncature, erreurs qui disent **quoi faire ensuite**.
- **MCP** (*Model Context Protocol*) : exposer outils et ressources de façon standard ; attention au coût en tokens des descriptions d'outils.
- **Cache de prompt** : ordonner le contexte du plus stable au plus variable pour maximiser les *cache hits*.

## À toi
> [!exercice] Audit de ton agent en production
> 1. Exporte 20 traces réelles et mesure la part de tokens par catégorie (système, outils, historique, résultats d'outils).
> 2. Identifie les 3 plus gros postes de gaspillage.
> 3. Applique **un** levier (compaction, troncature des retours, fusion d'outils) et compare avant/après sur ton jeu d'éval. Si tu n'en as pas encore, c'est [[A3 Évaluer les agents]] qui te le fera construire.
> 4. Note le résultat dans un *learning record*.

> [!source] Sources primaires
> - Anthropic, [Effective context engineering for AI agents](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents)
> - Anthropic Engineering : billet sur la conception d'outils pour agents, à lire sur le [blog Engineering](https://www.anthropic.com/engineering) (lien exact à vérifier)
> - [Spécification MCP](https://modelcontextprotocol.io/)

> [!prof] Une question ?
> Montre un de tes prompts système à ton agent-prof et demande une revue « à la bonne altitude ».
