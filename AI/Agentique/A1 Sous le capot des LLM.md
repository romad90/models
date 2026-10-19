# A1 Sous le capot des LLM

Retour : [[Piste Agentique]] · Précédent : [[A6 Sécurité des agents]] · Suivant : [[A5 Agents en production sur Google Cloud]]
Semaines : **S11–S13** (en même temps que [[M3 Deep learning]])

> [!examen] Pourquoi
> Tu utilises les LLM comme des boîtes noires. Comprendre tokenisation, attention, échantillonnage et entraînement t'aide à diagnostiquer les comportements bizarres, et c'est le genre de question qui revient en entretien.

## Diagnostic express
> [!quiz]- Pourquoi un LLM se trompe-t-il souvent pour compter les lettres d'un mot ?
> A) Il voit des tokens, pas des caractères individuels
> B) Il manque de données d'entraînement en orthographe
> C) Sa température est trop haute pendant le décodage
> D) Sa fenêtre de contexte est trop courte pour cela
>
> **Réponse : A.** La tokenisation (par exemple BPE) découpe le texte en sous-mots : le modèle ne « voit » pas directement les lettres.

## Notions
- **Tokenisation** (BPE), embeddings, **attention** et Transformer *decoder-only*
- **Pré-entraînement** (prédire le token suivant), puis **post-entraînement** : SFT, RLHF/DPO, RL avec récompenses vérifiables
- **Échantillonnage** : température, top-p ; pourquoi la température 0 n'est pas strictement déterministe (calcul en virgule flottante, *batching* côté serveur)
- **Inférence** : cache KV, latence du premier token et débit, coût du contexte long
- **Lois d'échelle** (*scaling laws*) et calcul au moment de l'inférence (*test-time compute*, raisonnement)

## À toi
> [!exercice] Comprendre en codant
> 1. Suis la vidéo d'Andrej Karpathy *Let's build GPT: from scratch* (YouTube) et entraîne un mini-GPT sur un petit corpus français.
> 2. Fais varier la température et observe les sorties.
> 3. Explique à ton agent-prof, avec tes mots, le rôle du cache KV dans le coût d'un agent à longue conversation.

> [!source] Sources primaires
> - [[CS224N]] : cours sur les Transformers et les LLM
> - [[CS336]] (*Language Modeling from Scratch*) : pour aller au fond, plutôt après la certification
> - 3Blue1Brown : série *Neural networks*, épisodes sur les Transformers et l'attention

> [!prof] Une question ?
> Demande à ton agent-prof un exercice chiffré sur l'attention avec 3 tokens.
