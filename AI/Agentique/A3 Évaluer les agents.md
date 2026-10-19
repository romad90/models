# A3 Évaluer les agents

Retour : [[Piste Agentique]] · Précédent : [[A2 Context engineering et outils]] · Suivant : [[A6 Sécurité des agents]]
Semaines : **S5–S8** (en même temps que les métriques de [[M2 ML classique]])

> [!examen] Pourquoi
> C'est **la** compétence qui distingue un AI Engineer senior, et le pont parfait avec le ML : une éval d'agent, c'est un jeu de test, des métriques et une analyse d'erreurs, exactement comme dans [[0002-train-validation-test|la leçon 2]] et [[0003-metriques-de-classification|la leçon 3]].

## Diagnostic express
> [!quiz]- Ton juge LLM dit que 92 % des réponses sont correctes. Que vérifier en premier ?
> A) La concordance du juge avec des annotations humaines
> B) La température utilisée par le juge pendant la notation
> C) Le nombre total de réponses évaluées par le juge
> D) La longueur moyenne des réponses notées par le juge
>
> **Réponse : A.** Un juge LLM est lui-même un classifieur : sans mesurer sa précision et son rappel face à un étiquetage humain, ses 92 % ne veulent rien dire. C compte aussi (intervalle de confiance), mais après.

## Notions (niveau avancé)
- **Partir des erreurs, pas des métriques** : lire 50 à 100 traces, catégoriser les échecs (*error analysis*), puis écrire une éval par catégorie qui compte.
- **Types d'évaluateurs** : assertions déterministes (format, appel du bon outil), comparaison à une référence, rubrique notée par un LLM, préférence par paires.
- **Juge LLM = classifieur** : le valider avec une **matrice de confusion** face à des humains et suivre précision et rappel. Voir [[Antisèche métriques]].
- **Évaluer la trajectoire autant que le résultat** : bons outils, bon ordre, nombre d'étapes, coût, et état final de l'environnement plutôt que texte final.
- **Statistiques** : les agents sont stochastiques. Faire plusieurs essais par cas (pass@k, pass^k), calculer des intervalles de confiance, ne pas conclure sur ±2 %.
- **Offline et online** : jeu d'éval de régression en CI, plus signaux de production (retours utilisateurs, taux d'escalade, échantillons annotés).
- **Séparer développement et test** : sinon tu sur-ajustes ton prompt à ton éval, c'est le *sur-apprentissage* de [[0002-train-validation-test|la leçon 2]].

## À toi
> [!exercice] Construire ton harnais d'éval (fil conducteur de 4 semaines)
> - **S5** : analyse d'erreurs sur 50 traces de production, puis une taxonomie de 4 à 6 catégories d'échecs.
> - **S6** : 30 à 50 cas de test (dont des cas limites), répartis entre un jeu de dev et un jeu de test gelé.
> - **S7** : un juge LLM pour la catégorie la plus subjective ; annote 40 cas toi-même et calcule précision et rappel du juge.
> - **S8** : branche l'éval en CI (elle échoue en cas de régression) et suis le coût par tâche.

> [!source] Sources primaires
> - Anthropic, [Building effective agents](https://www.anthropic.com/engineering/building-effective-agents)
> - [Berkeley Agentic AI MOOC](https://rdi.berkeley.edu/education) : cours sur l'évaluation des agents
> - Documentation de l'évaluation dans [ADK](https://google.github.io/adk-docs/) (critères : usage des outils, qualité de réponse, sécurité, succès de la tâche)

> [!prof] Une question ?
> Demande à ton agent-prof de relire ta taxonomie d'erreurs.
