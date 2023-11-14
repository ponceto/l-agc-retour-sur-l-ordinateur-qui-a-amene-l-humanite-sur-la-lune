# Script parties Romain

## Le contexte historique (2m30)

S'il y a un événement pour marquer l'aventure lunaire, c'est sans nul doute de discours de John Fitzgerald Kennedy donné le 25/05/1961 devant le Congrès américain. Il y demande l'approbation du budget pour réaliser un objectif nationnal ambitieux : amener un Américain sur la Lune avant la fin de la décennie.  
Pour bien comprendre cette décision, il faut se rappeler que nous sommes en pleine guerre froide, avec une forte rivalité entre États-Unis l'Union Soviétiques, et qu'il y a déjà tout un passif entre les deux blocs sur les questions spatiales.

Petit rappel des faits :  
Le 04/10/1957, Spoutnik (URSS) devient le 1er satellite artificiel en orbite, c'est un véritable choque pour les Américains car dans un contexte de menace nucléaire, ils deviennent vulnérable sur leur propre territoire.  
À cette époque, les États-Unis n'ont pas encore d'organisme capable de gérer un programme spatial d'ampleur, pour y remédier, il faut attendre la création de la NASA le 29/07/1958.  
Nouveau coup dur le 07/10/1959, la sonde soviétique LUNA 3 prend la 1er photographie de la face cachée de la Lune.  
Le coup de grâce arrive le 12/04/1961; Youri Gagarine (URSS) est le 1er homme dans l'espace.  
Trois semaines après Gagarine et 20 jours avant le discours de JFK, le 05/05/1961, Alan Shepard (USA) est le 1er Américain dans l'espace. **Mais**, là où Gagarine a réalisé une orbite complète autour de la Terre, Shepard lui se contente d'un vol suborbital. Comprennez : on l'a juste envoyé assez haut pour qu'il soit techniquement dans l'espace.  
Pour avoir un Américain en orbite terrestre, il faut attendre le vol de John Glenn (USA) le 20/02/1962.  

Les Américains sont en retard, et pour faire oublier ce retard ils ont besoin d'un exploit.  
La course à la Lune est un bon objectif, car elle nécessite un d'importants efforts économiques, industriels, mais aussi des avancées techniques et technologiques importantes, aussi bien côté Américain que Soviétique. Ceci est bénéfique pour les Américain car ça va leur permettre d'effacer leur retard.

---

## C'est quoi l'AGC ?

### Intro (15s)

Il est temps de vous parler de l'Apollo Guidance Computer, l'AGC.  

Mais pour mieux comprendre à quoi il sert l'AGC il faut comprendre le déroulé d'une mission lunaire :  

### Le déroulé d'une mission (1m30)

- Tout commence avec la mise en orbite terrestre du train lunaire rapidement suivi de l'injection translunaire.  
- 3 jours de transit Terre-Lune et des corrections de trajectoire.
- Arrivé jusqu'à la lune, le CM allume son moteur pour freiner et s'installer en orbite lunaire.
- Là, 2 des 3 astronautes montent à bord du LM qui se sépare alors du CM, le LM va faire une descente propulsive jusqu'à la surface.
- Une fois la mission à la surface terminée, le LM redécolle et va faire une succession de manoeuvre pour réaliser un rendez-vous orbital avec le CM.
- Une fois les astronautes et les roches transférés dans le CM, le LM est abandonné en orbite lunaire, le CM allume son moteur direction la Terre.
- 3 jours de transit Lune-Terre et des corrections de trajectoire
- La mission se termine avec la rentrée atmosphérique et l'amerrissage

Vous devez maintenant comprendre qu'une mission lunaire utilisait deux vaisseaux, chacun équipé d'un AGC.  

### L'échelle (20s)

Bien évidemment, le schéma n'est pas à l'échelle, la distance Terre-Lune est de 400 000 km. La précision nécessaire pour naviguer est donc très importante et trop élevée pour un humain.  

La mission première de l'AGC est donc la navigation.  

### C'est où le haut ? (1m)

La première question est : qu'elle est l'orientation du vaisseau/son attitude ?  
Sur Terre la gravité définit naturellement le bas et le haut et est un référentiel adapté à beaucoup de situations du quotidien.  
Dans l'espace, cette force est beaucoup moins adaptée à cause de l'apesanteur et parce que le vecteur gravité n'est pas fixe au cours d'une orbite.  
Pour s'orienter, l'AGC utilise une base de données intégrant la position d'étoiles comme points de référence. C'est un référentiel absolu, qui permet ensuite de se place dans le système Terre-Lune, connaitre l'orientation du vaisseau, etc.  
L'AGC utilise au total 5 référentiels adaptés aux différentes phases d'une mission lunaire.

### Où suis-je ? (1m)

Ensuite il faut savoir où l'on se trouve. L'AGC est capable le calculer sa position, mais les systèmes inertiels n'étant pas parfaits, des erreurs finissent par s'accumuler. Il faut pouvoir corriger ces erreurs.  
Pour corriger ces erreurs, les astronautes utilisaient un système d'optique pour faire des mesures d'angles entre des étoiles de référence et la ligne d'horizon d'objets comme la Lune. Avec ces angles, l'ordinateur est capable d'ajuster sa position.
On parle ici d'optiques avec une précision de 10 secondes d'arc.  
Ces techniques sont encore utilisées aujourd'hui, même sur les sondes les plus modernes.  

### Où vais-je ? (45s)

Il est important de comprendre que dans l'espace, n'importe quel corps est en chute libre.  
Les objets suivent des trajectoires balistiques qui décrivent des courbes, les trajectoires linéaires n'existent pas dans l'espace.  
L'AGC utilise 2 méthodes de calcul, l'une d'elles utilise des plans dans un cône pour obtenir n'importe quelle trajectoire possible.

### DAP (1m30)

La seconde mission de l'AGC est de gérer l'orientation et la propulsion du vaisseau.

Le DAP est un système de commande électrique qui permet à un programme ou un astronaute de définir une attitude souhaitée.  
Pour oritenter le vaisseau, on utilise les reaction control system (RCS). Sur la photo du module de commande et module de service, on les voit, ce sont les grappes de propulseurs sur les côtés du vaisseau.  
Le rôle du DAP est de calculer quels moteurs allumer, quand et combien de temps. Il doit intégrer les potentiels propulseurs HS, un retour d'expérience du programme Gemini, et la répartition de la masse du vaisseau.  

Pour rappel : une force qui passe par le centre de la masse d'un objet provoque une translation. Si cette force est excentrée, elle provoque plutôt une rotation de l'objet autour du centre de la masse.

L'emplacement des RCS reste fixe, mais les configurations et la répartition des masses très variées au cours d'une mission.

Pour vous donner un ordre d'idée de la complexité de ce problème, le DAP représente à lui seul 10% du code de l'AGC.

### Affichage (15s)

Le troisième rôle de l'AGC est de fournir de la donnée à l'équipage, que ce soit sur l'état des système ou encore des paramètres de vol.

### Liaison avec le sol et télémétrie (1min)

L'AGC n’est pas un système entièrement autonome, il intègre en cours de mission des données uploadées depuis le sol. Cela peut être par exemple des tâches de housekeeping, ou alors des paramètes pour une manoeuvre.  
Il envoie également des données sur son état au centre de contrôle, ce qui leur permettait d'analyser la bonne santé des systèmes, mais aussi de visualiser en direct ce que voyait et faisait l'équipage, une sorte de partage d'écran.  

---

## Le système

### Intro Margaret Hamilton

Vous devez connaitre Margaret Hamilton, elle était responsable de l'équipe du Draper Labotory du MIT à partir de 1970. C'est ce laboratoire qui a développé la centrale intertielle, mais aussi l'AGC, aussi bien du point de vue hardware que software.  

Le résultat de leurs travaux est un système mono-thread multiprocessus, adoptant des comportements que l'on peut qualifier de sofistiqués grace à un ensemble de mécaniques simples.  

### Le multiprocessing

Pourquoi utiliser le multiprocessing ? Pour les mêmes raisons qu'aujourd'hui. Cela permet de découper un problème complexe en des plus petits problèmes, plus simples à appréhender, développer et tester.  

À l'époque, il existait deux grandes stratégies pour gérer un système multi-process:  

- le "Cooperative multiprogramming", aka "je peux rendre la main"
- le "Preemptive multiprogramming", aka "ton temps CPU est terminé"  

L'AGC utilisait un mix de ces deux stratégies.

### L'executeur : le light OS

Pour administrer ces processus, l'AGC n'a pas d'OS à proprement parler, à la place il utilisait ce que l'on appel l'executeur.  

Le coeur de l'executer est constitué de 3 tables avec des adresses et des tailles fixes :  

- le core set qui contient les processus en cours d'exécution ainsi que des métadonnées associées tel que la priorité. 6 emplacements de 12 mots pour le CM, 7 pour le LM
- le VAC lui contient l'état des processus en cours d'exécution dans l'interpréteur, 5 emplacements de 44 mots
- la WAITLIST qui contient les processus programmé dans un futur proche ainsi que le temps restant avant de les démarrer

Pour administrer ces tables, il y a un ensemble de routines pour démarrer, stopper, programmer, changer la prioriter d'un processus, etc... Ces routines étaient appelées sur simple instruction processeur.

### L'executeur : le temps et les IO

Le suivi et la gestion du temps est important, on doit pouvoir démarrer des processus à des moments précis.  
Le processeur est accompagné d'un device pour alimenter des timers qui vont provoquer des interruptions de processus en cours.  
Par exemple le TIMER 3 permet de déclencher les jobs programmés dans la waitlist.  
Le TIMER 4 lançait des routines de vérification du hardware 8 fois par secondes.

Toutes ces interruptions provoquent des context switch : le processus en cours est interrompu, déchargé dans le VAC et le nouveau processus est chargé à la place. Ces interruptons ont donc un certain coût en cycles CPU et ne doivent pas survenir trop frequement.  

### Aparté : Les compteurs

Et là je dois faire une aparté pour parler des compteurs.  
Certains systèmes hardware liés à l'AGC servent à alimenter des compteurs, ces systèmes ont tendance à générer beaucoup d'I/O.  
Par exemple, les gyroscopes de la centrale inertielle ont une précision de 39 seconde d'arc, une rotation de quelques degrés/seconde du vaisseau peut ainsi rapidement provoquer des centaines voir plus d'un millier de signaux par seconde.
Spawner un nouveau processus pour chaque signal n'est donc pas adapté, notament à cause du coût du context switch.  

Pour contourner ce promblème, les ingénieurs ont mis en place un hack : le "cycle stealing".  

Ces systèmes hardwares sont interfacés avec l'AGC par de biais de Coupling Data Unit (CDU), ceux-ci envoient des "pulses" dans des registres dédiés du CPU.  
Quand le CPU détecte un de ces pulses, il va "voler" son prochain cycle au processus en cours d'exécution pour aller incrémenter/décrémenter en mémoire vive le compteur correspondant au registe. L'opération reste totalement transparente pour le processus en cours.  

### Exécuteur : Gestion des erreurs

Le dernier rôle de l'exécuteur est la gestion des erreurs, aucun système n'est parfait, et l'AGC ne fait pas exception.  

En cas de plantage d'un processus, il existe trois scénarios possibles :  

- P00DOO : le processus n'est pas très important et est stoppé sans tentative de redémarrage  
- software restarts : le processus est plus critique et doit être redémarré, s'en suis tout une séquence d'interruption des processus, de néttoyage des tables (core set, VAC, waitlist) de l'exécuteur avant de redémarrer les processus
- AGC "fresh start" : arrive si le software restarts échoue, tout est nettoyé jusqu'au hardware, l'AGC est placé dans un état "Idle" et implique des opérations de la part des astronautes. On veut à tout prix éviter d'en arriver là.

Dans le cas du software restart, il y a deux possibilités :  

- le programme est peut coûteux en temps de calcul et on peut se permettre de l'éxecuter en totalité  
- le programme est coûteux et l'on va vouloir le redémarrer à au milieu de son exécution avec un état connu  

Pour rédémarrer un processus, l'exécuteur utilise donc plusieurs tables :  

- les Group table & Restart table en mémoire morte qui stockent la logique
- la phase table en mémoire vive

La phase table stocke les paramètres nécessaires pour redémarrer les processus.  
Elle a également un second rôle important, le MODREG qui permet de stocker le Major mode dans lequel se trouve l'AGC.  
De façon simple, le major mode correspond à un processus long spécifique à une phase spécifie de la mission, on y reviendra.

### Interpréteur

Tout ce que j'ai évoqué jusqu'à maintenant est codé en assembleur, nommé "Basique" par les ingénieur. (Aucun lien avec le langage du même nom)  
Pour permettre de s'abstraire des limitations du processeur et du Basique, l'AGC est doté de l'interpreteur, une architecture CPU "logicielle".  

Elle apporte de nouvelles capacités comme les vecteurs ou encore des fonctions arithmétiques et trigonométriques.

Cette surcouche ajoute un surcoût en ressources CPU, par exemple pour des opérations trigonométriques: SIN = 5.6ms; ACOS = 9.1ms.  

C'est pour cette raison que les processus peuvent mélanger du code assembleur et du code exécuté sur l'interpreteur pour maximiser l'usage des ressources et la performance.  

### Langage de haut niveau

L'interpreteur est également pensé pour être utilisé avec son langage de haut niveau, l'interpretive.  
Là aussi, rien à voir avec nos langages modèrnes compilés. Il s'agit d'une forme d'assembleur, mais avec des instructions de plus haut niveau pour manipuler les types "complexes" de l'interpreteur.  
A l'écran on peut par exemple voir des racines carrés (SQRT), des soustractions (DSU) ou encore des divisions (DDV).  

Enfin, les traitements sont exprimés sous la forme d'expressions qui peuvent être parcourus sous la forme d'arbres.  
Cela a un gros avantage sur la gestion de la mémoire facilité car une simple stack/pile suffit. En parcourant l'arbre, on ajoute les états intermédiaire dans la stack, et quand on a besoin d'en récuppérer un, il s'agit forcément de l'élément en au de la pile.

---

## Les principaux incidents

Je vais maintenant vous parler des deux principaux incidents de vol qui ont impliqué l'AGC.

### Apollo 11

Le premier a eu lieu au cours de la mission Apollo 11 : on est à bord du module lunaire, en pleine descente propulsive a environ 33000 pieds au-dessus de la surface (l'altitude à laquelle vol un avion de ligne).  
Tout se déroule bien quand soudain le master alarme sonne. Program alarm, 1202.  

Il faut bien comprendre que la descente vers la lune est une phase de la mission avec ce qui est peut-être la plus grosse charge de travail pour l'AGC : en plus des tâches de fond, il doit gérer la navigation, l'attitude, la propulsion, intégrer beaucoup d'I/O issue de l'IMU et de la radio sonde.  

Un autre systeme mis sous tension mais en stand-by est le radar de rdv, il doit être prêt en cas d'abandon de la descente.  

L'origine du problème est un malheureux déphasage électrique entre le CDU du radar de rdv et l'AGC.  
La conséquence de ce déphasage est un AGC qui va se faire flooder par les pulses, environ 15% du temps CPU est alors alloué aux cycle stealing.  
Les processus en cours sont donc ralentis et commencent à mettre trop de temps à être exécutés.  

À partir de là, il n'est plus qu'une question de temps avant que l'AGC ne tente de démarrer un nouveau processus alors que le coreset ou le VAC est plein : Executive overflow, program alarm.  

Ce type d'erreur va avoir lieu à 5 reprises au cour de la descente :  

- 4 alarmes 1202 pour un core set plein
- 1 alarme 1201 pour un VAC plein

Fort heureusement la séquence de "software restart" va s'exécuter avec succès à chaque fois et l'AGC reprend son travail sans incidence majeur pour la descente.  
Ceci a tout de même été une source de stress supplémentaire pour les astronautes, d'autant que sur un redémarrage, l'affiage du DSKY a été perdu pendant une dizaine de seconde alors qu'il devait fournir des informations critiques sur les paramètres de vol.  

### Apollo 14 

### Transcript

Le second incident majeur a eu lieu au cours d'Apollo 14. Nous somme de nouveau à bord du LM mais cette fois-ci en orbite lunaire.  
Pendant que les astronautes préparent le LM pour la descente, les équipes à Huston analysent les données et constatent une anomalie : le bit du "abort button" est à 1.  

Après quelques manipulations demandées à l'équipage, il est conclu que le bouton est fautif. On suspecte un débrit de soudure qui flotte dedans et crée des contacts intermittents.  

Si cela se produit au cours de la descente alors la mission sera un échec. En quelques heures, les ingénieurs vont fournir une solution de contournement.  

Par défaut, le bouton est inhibé par un simple bit en mémoire vive, celui-ci est modifié au moment de l'allumage du moteur de sorte à rendre le bouton actif.  
Modifier le programme n'est pas possible puisqu'il est inscrit dans la CORE ROPE.  
Il est par contre possible de le désactiver via quelques instructions sur le DSKY, mais le temps de réaliser cette manipulation, un contact peut être détecté.  

### Les controles

En cas de contact, on effectue deux vérifications avant d'interompre la descente :  

- Le bouton est-il actif ? Il s'agit du bit que l'on souhaite modifier.  
- Est-on déjà entrain d'abandonner l'alunissage ? Pour se faire on va lire le major mode inscrit dans le MODREG.  

Le but va donc être de faire croire à l'AGC qu'il est déjà dans une logique d'abandon le temps de la modification du bit.  

Le hack repose sur un détail de design de l'AGC : le major mode inscrit dans le MODEREG n'est pas nécessairement le major mode réellement executé par l'ordinateur.  

### Le hack

Les astronautes, par le biais du DSKY, vont donc aller modifier cette valeur et y inscrire 71 (major mode d'abandon) avant le démarrage du moteur. Ainsi en cas de contact, la seconde vérification de la routine va empêcher l'abandon.  
Une fois le moteur démarré, les astronautes vont modifier le bit de sorte à désactiver le bouton, puis ils vont réinscrire le programme d'origine dans le MODREG : 63.

En cas de nécessité abort, les astronautes pouvaient toujours démarrer manuellement le programme d'abandon : VERB 37 ENTER 71 ENTER

En cas de nécessité abort, ils pouvaient toujours remodifier le LETABORT ou alors manuellement démarrer le programme correspondant : VERB 37 ENTER 71 ENTER

---

## Conclusion

L'aventure lunaire est le résultat de contextes historique et technologique propices.  
L'informatique a indéniablement joué un rôle clé dans le succès du programme Apollo.  
Les briques technologiques nécessaires à un projet comme l'AGC vennaient d'être débloquées (les transitors), il est peu probable que l'AGC eu été possible une décénnie plus tôt.  
Au moment où JFK a prononcé son discours, l'informatique était émergent à la NASA. Les calculs qui ont permis le premier vol d'Alan Shepard étaient encore réalisés par une armée de calculatrices humaines, des personnes, en majorité des femmes, dont le métier était de réaliser à la main ces calculs.  
Moins de dix ans après, le 20 juillet 1969 Armstrong et Aldrin posent le pied sur la Lune grace un ordinateur assé compacte pour tenir dans un module habité. À la fin du programme Apollo, l'AGC était un ordinateur dépassé.  
Les ingénieurs qui ont travaillé.e.s sur l'AGC, aussi bien l'ordinateur que la chaine des production des composants en amont, ont été des pionnères et des pionners sur tout un ensemble de problématiques. Leurs solutions ont pu profiter à l'ensemble de notre industrie.  
Le programme Apollo a donc été un formidable accélerateur (et non une étape indispensable) pour le développement de l'électronique et de l'informatique morderne.  
Si parfois vous vous intérrogez sur l'utilité de financer de tels programmes, souvennez-vous qu'ils impliquent de la recherche et des développements de technologies nouvelles qui peuvent par la suite trouver des applications dans votre quotidien.  
