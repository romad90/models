# A5 Agents en production sur Google Cloud

Retour : [[Piste Agentique]] · Précédent : [[A1 Sous le capot des LLM]] · Suivant : [[A4 Orchestration multi-agents]]
Semaines : **S14–S17** (en même temps que [[M4 Google Cloud et Agent Platform]] et [[M7 Servir les modèles]])

> [!examen] Pourquoi
> Tu as déjà des agents en production : ce module transpose ce savoir-faire sur **Gemini Enterprise Agent Platform**, qui est au cœur de l'examen 2026. Tu y ajoutes les réflexes d'exploitation d'un ingénieur senior.

## Diagnostic express
> [!quiz]- Quel levier réduit le plus le coût d'un agent à prompt système long et stable ?
> A) Activer le cache de prompt sur la partie stable du contexte
> B) Augmenter la taille maximale des réponses générées par l'agent
> C) Ajouter des exemples few-shot supplémentaires au prompt système
> D) Répéter les instructions importantes à la fin de chaque message
>
> **Réponse : A.** Un préfixe stable mis en cache est facturé bien moins cher et accélère le premier token. B, C et D augmentent le nombre de tokens.

## Notions
- **Pile Google** : Agent Development Kit (**ADK**), Agent Runtime (ex-Agent Engine) pour héberger, Agent Studio pour prototyper, Model Garden pour choisir le modèle, voir [[Correspondance des noms Vertex AI]]
- **Interopérabilité** : **MCP** (outils et ressources) et **A2A** (*Agent2Agent*, communication entre agents)
- **Alternatives d'hébergement** : Cloud Run et GKE, quand préférer chacun à Agent Runtime
- **Exploitation** : versions de prompts et de modèles, déploiement progressif, retour arrière, traces (OpenTelemetry, Cloud Trace), coût par tâche, limites de débit (*rate limits*), *fallbacks* entre modèles
- **Optimiser coût et latence** : routage vers un petit modèle, cache de prompt, appels d'outils en parallèle, traitement par lots pour l'asynchrone

## À toi
> [!exercice] Porter un de tes agents sur Agent Platform
> 1. Réécris un petit agent existant avec ADK, avec au moins 2 outils dont un serveur MCP.
> 2. Déploie-le sur Agent Runtime (ou Cloud Run), avec traces et un tableau de bord coût/latence.
> 3. Rejoue ton éval de [[A3 Évaluer les agents]] contre la version déployée.
> 4. Compare avec ta pile actuelle dans un *learning record* : ce qui est mieux, ce qui manque.

> [!source] Sources primaires
> - [Documentation ADK](https://google.github.io/adk-docs/)
> - [Documentation Gemini Enterprise Agent Platform](https://docs.cloud.google.com/gemini-enterprise-agent-platform)
> - [Protocole A2A](https://a2a-protocol.org/) (lien à vérifier)

> [!prof] Une question ?
> Demande à ton agent-prof un exercice d'*agent system design* chronométré (45 minutes).
