# A6 Sécurité des agents

Retour : [[Piste Agentique]] · Précédent : [[A3 Évaluer les agents]] · Suivant : [[A1 Sous le capot des LLM]]
Semaines : **S9–S10**

> [!examen] Pourquoi
> Un agent qui lit du contenu externe **et** agit (envoie un email, écrit du code, paie) est une surface d'attaque. Les recruteurs vérifient que tu sais raisonner en modèle de menace. L'examen PMLE couvre aussi IAM et la protection des données ([[Domaine 6 Monitorer les solutions IA]]).

## Diagnostic express
> [!quiz]- Quelle combinaison rend une injection indirecte de prompt vraiment dangereuse ?
> A) Accès aux données privées, contenu non fiable et exfiltration possible
> B) Modèle très récent, longue fenêtre de contexte et température élevée
> C) Prompt système court, peu d'outils et absence de mémoire persistante
> D) Utilisateurs nombreux, trafic élevé et déploiement sur plusieurs régions
>
> **Réponse : A.** Quand les trois se cumulent (données sensibles, entrée non fiable, canal de sortie), un texte malveillant peut faire fuiter des données. On casse le risque en retirant au moins un des trois.

## Notions
- **Injection directe et indirecte** : l'instruction malveillante arrive par l'utilisateur, ou par une page web, un email, un résultat d'outil ou un fichier.
- **Défense en profondeur** : moindre privilège pour les outils et les identifiants, validation humaine des actions irréversibles, bacs à sable (*sandboxing*), listes blanches réseau, séparation des données et des instructions, filtrage des sorties.
- **Hypothèse réaliste** : aucun filtre n'est fiable à 100 %, donc on limite **ce que l'agent peut faire**, pas seulement ce qu'il lit.
- **Autres risques** : fuite de prompt système, empoisonnement de mémoire ou de RAG, outils MCP tiers malveillants, déni de portefeuille (boucles coûteuses).
- **Côté Google Cloud** : comptes de service dédiés, VPC Service Controls, Model Armor, Sensitive Data Protection (noms de produits à vérifier dans la doc actuelle).

## À toi
> [!exercice] Red team de ton propre agent
> 1. Dessine le modèle de menace de ton agent en production : entrées non fiables, données sensibles, actions possibles.
> 2. Écris 10 cas d'attaque (dont 5 indirects) et ajoute-les à ton éval de [[A3 Évaluer les agents]].
> 3. Corrige le pire cas en **réduisant une capacité**, puis vérifie que l'éval passe.

> [!source] Sources primaires
> - [OWASP Top 10 for LLM Applications](https://genai.owasp.org/llm-top-10/)
> - [Berkeley Agentic AI MOOC](https://rdi.berkeley.edu/education) : cours sur la sûreté et la sécurité des agents

> [!prof] Une question ?
> Décris un de tes outils à ton agent-prof et demande-lui comment il l'attaquerait.
