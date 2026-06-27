# L'IA dans le produit : de l'appel LLM simple aux architectures multi-agents
 
Présentation technique (~35 min) qui retrace, étape par étape, la montée en complexité des architectures d'IA dans un produit : du simple appel à un LLM jusqu'aux équipes d'agents orchestrées. Chaque partie ajoute une capacité par rapport à la précédente, avec des schémas animés et des cas d'usage concrets.
 
> Présentée par Mohammed BEN SAID — illustrée avec le Microsoft Agent Framework.
 
## Sujet et objectif
 
L'objectif est de clarifier le vocabulaire et les architectures de l'IA appliquée au produit, en montrant ce que chaque approche apporte et ses limites :
 
- Quand un simple appel LLM suffit, et comment le prompting le pousse au maximum sans le rendre agentique.
- Ce qu'est réellement un agent (boucle ReAct, outils, mémoire) et pourquoi l'agent — et non le LLM — joue le rôle de mémoire et d'orchestrateur.
- Comment composer plusieurs agents et quels patterns d'orchestration utiliser pour des workflows fiables.
## Plan de la présentation
 
La présentation est structurée en 3 parties (12 slides au total).
 
### Partie 1 · Approche non agentique
 
Un seul appel au modèle, sans boucle ni outil.
 
- **Le LLM direct** — une question, une réponse. L'architecture la plus simple : un appel, un résultat.
- **Prompting avancé** — maximiser le LLM sans agent. Cinq mécanismes illustrés sur un cas concret : *System prompt*, *Few-shot*, *RAG simple*, *Chain of Thought*, *Structured output (JSON)*. On y montre la construction du prompt final envoyé au modèle, puis sa réponse structurée.
### Partie 2 · Approche agentique
 
Le modèle décide des actions ; l'agent exécute, mémorise et orchestre.
 
- **Mono-agent : la boucle ReAct** — diagramme de séquence (User → Agent → LLM → Outils). Point clé : le LLM étant sans mémoire, l'agent reconstruit et renvoie tout le contexte à chaque appel.
- **Multi-agent : l'agent-as-tool** — un agent principal utilise des sous-agents spécialisés comme outils et gère sa propre mémoire, distincte de l'historique de conversation.
- **Garde-fou en entrée : le modérateur** — un mini-agent classifieur intercepte les requêtes hors-périmètre avant qu'elles n'atteignent l'agent principal.
- **Garde-fou en sortie : l'agent juge** — un juge évalue la réponse de l'agent ; s'il la rejette, l'agent la régénère avec le feedback (pattern *critic-actor*).
### Partie 3 · Workflow & Orchestration
 
Composer plusieurs agents selon des patterns éprouvés, avec des cas réels.
 
- **Sequential** — pipeline mixant agents IA et code classique, chaque étape dépendant de la précédente. *Cas : assistant de tri des déchets.*
- **Concurrent** — plusieurs agents traitent le même input en parallèle (*fan-out*), puis agrégation des résultats (*fan-in*). *Cas : enrichissement d'un avis après achat.*
- **Group Chat** — un manager IA lit la conversation et choisit le prochain agent (sélection *prompt-based*). *Cas : assistant de support client.*
- **Handoff** — les agents se passent le relais directement, sans coordinateur central ; le prochain agent dépend du contenu. *Cas : support bancaire.*
## Consultation
 
La présentation est fournie sous forme d'un fichier HTML dynamique et autonome (`presentation-slides.html`), sans dépendance à installer ni connexion internet requise. Pour la consulter, téléchargez le fichier puis ouvrez-le dans un navigateur web moderne (Chrome, Edge, Firefox, Safari). La navigation se fait avec les flèches du clavier.
 
## Auteur
 
Mohammed BEN SAID
 
## Contenu du dépôt
 
```
.
├── presentation-slides.html   # La présentation (à ouvrir dans un navigateur)
└── README.md                  # Ce fichier
```
 
