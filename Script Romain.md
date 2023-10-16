# Le contexte historique (2m30)

S'il y a un événement pour marquer l'aventure lunaire, c'est sans nul doute de discours de John Fitzgerald Kennedy donné le 25/05/1961 devant le Congrès américain. Il y demande l'approbation du budget pour réaliser un objectif nationnal ambitieux : amener un Américain sur la Lune avant la fin de la décennie.  
Pour bien comprendre cette décision, il faut se rappeler que nous sommes en pleine guerre froide, avec une forte rivalité entre États-Unis l'Union Soviétiques.

Petit rappel des faits :  
Le 04/10/1957, Spoutnik (URSS) devient le 1er satellite artificiel en orbite, c'est un véritable choque pour les Américains car dans un contexte de menace nucléaire, ils deviennent vulnérable sur leur propre territoire.  
À cette époque, les États-Unis n'ont pas encore d'organisme capable de gérer un programme spatial nationnal, pour y remédier, il faut attendre la création de la NASA le 29/07/1958.  
Nouveau coup dur le 07/10/1959, la sonde soviétique LUNA 3 prend la 1er photographie de la face cachée de la Lune.  
Le coup de grâce arrive le 12/04/1961; Youri Gagarine (URSS) est le 1er homme dans l'espace.  
Trois semaines après Gagarine et 20 jours avant le discours de JFK, le 05/05/1961, Alan Shepard (USA) est le 1er Américain dans l'espace. **Mais**, là où Gagarine a réalisé une orbite complète autour de la Terre, Shepard lui se contente d'un vol suborbital. Comprennez : on l'a juste envoyé assez haut pour qu'il soit techniquement dans l'espace.  
Pour avoir un Américain en orbite terrestre, il faut attendre le vol de John Glenn (USA) le 20/02/1962.  

Les Américains sont en retard, et pour faire oublier ce retard ils ont besoin d'un exploit.  
La course à la Lune est un bon objectif, car elle nécessite un d'importants efforts économiques, industriels, mais aussi des avancées techniques et technologiques importantes, aussi bien côté Américain que Soviétique. Ceci est bénéfique pour les Américain car ça va leur permettre d'effacer leur retard.


---

# C'est quoi l'AGC ?

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

La première question est : comment s'orienter ? Sur Terre la gravité définit naturellement le bas et le haut et est un référentiel adapté à beaucoup de situations du quotidien.  
Dans l'espace, cette force est beaucoup moins adaptée à cause de l'apesanteur et parce que le vecteur gravité n'est pas fixe au cours d'une orbite.   
Pour s'orienter, l'AGC utilise une base de données intégrant la position d'étoiles comme points de référence.  
L'AGC utilise au total 5 référentiels adaptés aux différentes phases d'une mission lunaire.

### Où suis-je ? (1m)

Ensuite il faut savoir où l'on se trouve. L'AGC est capable le calculer sa position, mais les systèmes inertiels n'étant pas parfaits, des erreurs finissent par s'accumuler. Il faut pouvoir corriger ces erreurs.  
Les astronautes faisaient de la navigation aux étoiles pour connaitre leur position exacte. On parle ici d'optiques avec une précision de 10 secondes d'arc.  
Ces techniques sont encore utilisées aujourd'hui, même sur les sondes les plus modernes.  

### Où vais-je ? (45s)

Il est important de comprendre que dans l'espace, n'importe quel corps est en chute libre. Cela implique qu'être immobile est impossible, et que les objets suivent des trajectoires balistiques.  
L'AGC intègre donc les accélérations mesurées par la centrale inertielle pour calculer la trajectoire du vaisseau.  
Il utilise 2 méthodes de calcul, l'une d'elles utilise des plans dans un cône pour obtenir des trajectoires approximatives.

### DAP (1m30)

La seconde mission de l'AGC est de gérer l'orientation et la propulsion du vaisseau.

Le DAP est un système de commande électrique qui permet à un programme ou un astronaute de définir une attitude souhaitée sans se préoccuper des RCS. (montrer) Les RCS sont des petits propulseurs sur les côtés du vaisseau.  
Le rôle du DAP est de calculer quels moteurs allumer, quand et combien de temps. Il doit intégrer les potentiels propulseurs HS, un retour d'expérience du programme Gemini, et la répartition de la masse du vaisseau.  

Pour rappel : une force qui passe par le centre de la masse d'un objet provoque une translation. Si cette force est excentrée, elle provoque plutôt une rotation de l'objet autour du centre de la masse.

L'emplacement des RCS reste fixe, mais les configurations et la répartition des masses très variées au cours d'une mission.

Pour vous donner un ordre d'idée de la complexité de ce problème, le DAP représente à lui seul 10% du code de l'AGC.

### Affichage (15s)

Le troisième rôle de l'AGC est de fournir de la donée à l'équipage, que ce soit sur l'état des système ou encore des paramètres de vol.

### Liaison avec le sol et télémétrie (1min)

L'AGC n’est pas un système entièrement autonome, il intègre en cours de mission des données uploadées depuis le sol.  
Il envoie également des données sur son état au centre de contrôle, ce qui leur permettait d'analyser l'état du vaisseau, mais aussi de visualiser en direct ce que voyait et faisait l'équipage, une sorte de partage d'écran.  


---

# Le système

### Intro Margaret Hamilton

Vous devez connaitre Margaret Hamilton, elle était responsable de l'équipe du Draper Labotory du MIT à partir de 1970. C'est ce laboratoire qui a développé la centrale intertielle, mais aussi l'AGC, aussi bien du point de vue hardware que software.  

Le résultat de leurs travaux est un système multiprocessus, adoptant des comportements que l'on peut qualifier de sofistiqués grace à un ensemble de mécaniques simples.  

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

Le suivi et la gestion du temps est important, le processeur est accompagné d'un device pour alimenter des timers qui vont provoquer des interruptions de processus en cours.  
Par exemple le TIMER 3 permet de déclencher les jobs programmés dans la waitlist.  
Le TIMER 4 lançait des routines de vérification du hardware 8 fois par secondes.

Toutes ces interruptions provoquent des context switch : le processus en cours est interrompu, déchargé dans le VAC et le nouveau processus est chargé à la place. Ces interruptons ont donc un certain coût en cycles CPU et ne doivent pas survenir trop frequement.  

### Aparté : Les compteurs

Et là je dois faire une aparté pour parler des compteurs.  
Certains appareils peuvent générer beaucoup d'I/O sous la forme de ticks qui vont incrémenter ou décrémenter des compteurs.  
Par exemple les gyroscopes de la centrale inertielle ont une précision de 39 seconde d'arc, une rotation de quelques degrés/seconde du vaisseau peut ainsi rapidement provoquer des centaines voir des milliers d'interruptions, ce qui ne peut pas être géré en context switch.  

Pour contourner ce promblème, les ingénieurs ont mis en place un hack : le "cycle stealing".  

Pour des opérations I/O visant a incrémenter/décrémenter des compteurs, le hardware envoie des "pulses" dans des registres dédiés du CPU.  
Quand le CPU détecte un de ces pulses, il va "voler" son prochain cycle au processus en cours d'exécution pour aller incrémenter/décrémenter en mémoire vive le compteur impacté. L'opération reste totalement transparente pour le processus en cours.  

### Exécuteur : Gestion des erreurs

Le dernier rôle de l'exécuteur est la gestion des erreurs, aucun système n'est parfait, et l'AGC ne fait pas exception.  

En cas de plantage d'un processus, il existe trois scénarios possibles :  
- P00DOO : le processus n'est pas très important et est stoppé sans tentative de redémarrage  
- software restarts : le processus est plus critique et doit être redémarré, s'en suis tout une séquence d'interruption des processus, de néttoyage des tables de l'exécuteur avant de redémarrer les processus
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


# Les principaux incidents

Je vais maintenant vous parler des deux principaux incidents de vol qui ont impliqué l'AGC.

### Apollo 11

Le premier a eu lieu au cours de la mission Apollo 11 : on est à bord du module lunaire, en pleine descente propulsive a environ 33000 pieds au-dessus de la surface (l'altitude à laquelle vol un avion de ligne).  
Tout se déroule bien quand soudain le master alarme sonne. Program alarm, 1202.  

Il faut bien comprendre que la descente vers la lune est une phase de la mission avec ce qui est peut-être la plus grosse charge de travail pour l'AGC : il doit gérer la navigation, la propulsion, intégrer les données de l'IMU et de la radio sonde.  

Il faut également que des systèmes comme le radar de rdv soient prêts en cas d'abandon de la descente.

L'origine du problème est un malheureux déphasage électrique entre le radar de rdv et l'AGC.  
La conséquence de ce déphasage est un AGC qui va se faire flooder par les pulses, environ 15% du temps CPU est alors alloué aux cycle stealing.  
Les processus en cours sont donc ralentis et commencent à mettre trop de temps à être exécutés.  

À partir de là, il n'est plus qu'une question de temps avant que l'AGC ne tente de démarrer un processus de la WAITLIST alors que le coreset est plein : Executive overflow, program alarm, 1202.  

Ce type d'erreur va avoir lieu à 5 reprises au cour de la descente. Fort heureusement la séquence de "software restart" va s'exécuter avec succès à chaque fois et l'AGC reprend son travail sans incidence majeur pour la descente.

### Apollo 14

### Transcript

Le second incident majeur a eu lieu au cours d'Apollo 14. Nous somme de nouveau à bord du LM mais cette fois-ci en orbite lunaire.  
Pendant que les astronautes préparent le LM pour la descente, les équipes à Huston analysent les données et constatent une anomalie : le bit du "abort button" est à 1.  

Après quelques manipulations demandées à l'équipage, il est conclu que le bouton est fautif. On suspecte un débrit de soudure qui flotte dedans et crée des contacts intermittents.  

Si cela se produit au cours de la descente alors la mission sera un échec. En quelques heures, les ingénieurs vont fournir une solution de contournement.  

### Les éléments

Pour comprendre la solution trouvée, il faut quelques éléments :  
- la routine 11 : elle vérifie tous les 1/4 de seconde si le bouton est appuyé
- le LETABORT bit est un bit en mémoire qui permet d'inhiber le "abort button"
- le P63 : est le premier programme de la séquence de 3 programmes qui composent l'alunissage, il gère notamment la phase d'allumage des moteurs "sobrement" appelé BURNBABY
- les P70 & P71 sont des programmes d'abandons
- le MODREG (phase table) qui contient le major mode

### La séquence d'abort

Une séquence normale se déroule de la façon suivante :
- les astronautes démarrent le P63, ce qui va inscrire le major mode 63 dans le MODREG
- environ 15 minutes plus tard se lance le BURNBABY, avec le démarrage du moteur, le LETABORT est set, le bouton n'est plus inhibé
- la routine 11 vérifie l'état du bouton
- s’il y a contact, alors elle vérifie le LETABORT
- le LETABORT ne bloque pas, R11 vérifie alors le major mode en cours
- comme le major mode n'est pas P70 ni P71, c'est que l'abort n'a pas encore été déclenché
- le P63 est stoppé et le P71 démarré

Le hack trouvé repose sur aspect de design de l'AGC : il n'y a pas de corrélation entre le major mode stocké dans le MODREG et le major mode réellement exécuté.  

### Le hack

Le but du hack est de faire croire à l'AGC qu'il est déjà dans une séquence d'abort.  
- les astronautes démarrent le P63, ce qui va inscrire le major mode 63 dans le MODREG
- les astronautes vont alors modifier le MODREG et y inscrire le major mode 71
- une fois la phase BURNBABY démarrée, s’il y a contact, alors la routine 11 ne déclenchera pas le P71 car elle pensera qu'elle est déjà en cours d'exécution
- les astronautes vont alors modifier le LETABORT bit pour de nouveau inhiber le bouton
- enfin les astronautes vont de nouveau inscrire P63 dans le MODREG pour le bon fonctionnement de l'AGC

En cas de nécessité abort, ils pouvaient toujours remodifier le LETABORT ou alors manuellement démarrer le programme correspondant.


---

# Conclusion

L'aventure lunaire est le résultat de contextes historique et technologique propices.  
L'informatique a indéniablement joué un rôle clé dans le succès du programme Apollo.  
Les briques technologiques nécessaires à un projet comme l'AGC vennaient d'être débloquées, il est peu probable que l'AGC eu été possible une décénnie plus tôt.  
Au moment où JFK a prononcé son discours, l'informatique était émergent à la NASA. Les calculs qui ont permis le premier vol d'Alan Shepard étaient encore réalisés par une armée de calculatrices humaines, des personnes, en majorité des femmes, dont le métier était de réaliser ces calculs.  
Moins de dix ans après, un ordinateur assé comptacte pour tenir dans une capsule arrivait sur la surface de la Lune. À la fin du programme Apollo, l'AGC était un ordinateur dépassé.  
Les ingénieurs qui ont travaillé.e.s sur l'AGC ont été des pionnères et des pionners sur tout un ensemble de problématiques. Leurs solutions ont pu profiter à l'ensemble de notre industrie.  
Le programme Apollo a donc été un formidable accélerateur pour le développement de l'électronique et de l'informatique morderne.  
