# Le contexte historique (2m30)

S'il y a un événement pour marquer l'aventure lunaire, c'est sans nul doute de discours de John Fitzgerald Kennedy donné le 25/05/1961 devant le Congrès américain. Il y demande l'approbation du budget pour un objectif ambitieux : amener un Américain sur la Lune avant la fin de la décennie.  
Pour bien comprendre cette décision, il faut se rappeler que nous sommes en pleine guerre froide, et que les États-Unis accusent un important retard sur les Soviétiques sur tout ce qui touche au spatial.

Petit rappel des événements : 
- le 04/10/1957 : Spoutnik (URSS) est le 1er satellite artificiel en orbite, c'est un véritable choque pour les Américains
- à cette époque, les États-Unis n'ont même pas de programme spatial national, pour y remédier, il faut attendre la création de la NASA le 29/07/1958 
- le 07/10/1959, nouveau coup de massue : la sonde soviétique LUNA 3 prend la 1er photographie de la face cachée de la Lune
- le coup de grâce arrive le 12/04/1961 : Youri Gagarine (URSS) est le 1er homme dans l'espace, il réalise une orbite complète autour de la Terre
- Seulement 3 semaines après Gagarine et 20 jours avant le discours de JFK, le 05/05/1961, Alan Shepard (USA) est le 1er Américain dans l'espace. **Mais** il s'agit d'un vol suborbital (aka: on l'a juste envoyé assez haut pour qu'il soit techniquement dans l'espace).
- pour avoir un Américain en orbite terrestre, il faut attendre le vol de John Glenn (USA) le 20/02/1962 

Les Américains sont en retard, et pour faire oublier ce retard ils ont besoin d'un exploit.  
La course à la Lune est un bon objectif, car elle nécessite un budget colossal, des avancées techniques et technologiques importantes, même pour les Soviétiques, ce qui gommerait leur avance.


---

# C'est quoi l'AGC ?

### Intro (15s)

Il est temps de vous parler de l'Apollo Guidance Computer, l'AGC.  

Une mission ne comporte pas un mais deux AGC, un dans le CM et un dans le LM.  

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

### L'échelle (20s)

Le schéma n'est pas à l'échelle, la distance Terre-Lune est de 400 000 km. La précision nécessaire pour naviguer est donc très importante.  

La mission première de l'AGC est donc la navigation.  

### C'est où le haut ? (1m)

La première question est : comment s'orienter ? Sur Terre la gravité définit naturellement le bas et le haut et est un référentiel adapté à beaucoup de situations du quotidien.  
Dans l'espace, cette force est beaucoup moins adaptée à cause de l'apesanteur et parce que le vecteur gravité n'est pas fixe au cours d'une orbite.   
On utilise le système Terre-Lune ainsi que des étoiles comme points de références.  
L'AGC intègre 5 référentiels adaptés aux différentes phases d'une mission lunaire.

### Où suis-je ? (1m)

Ensuite il faut savoir où l'on se trouve. L'AGC est capable le calculer sa position, mais les systèmes inertiels n'étant pas parfaits, des erreurs finissent par s'accumuler. Il faut pouvoir corriger ces erreurs.  
Les astronautes faisaient de la navigation aux étoiles pour connaitre leur position exacte. On parle ici d'optiques avec une précision de 10 secondes d'arc.  

### Où vais-je ? (45s)

Il est important de comprendre que dans l'espace, n'importe quel corps est en chute libre. Cela implique qu'être immobile est impossible, et que les objets suivent des trajectoires balistiques.  
L'AGC intègre donc les accélérations mesurées par la centrale inertielle pour calculer la trajectoire du vaisseau.  
Il utilise 2 méthodes de calcul, l'une d'elles utilise des plans dans un cône pour obtenir des trajectoires approximatives.

### DAP (1m30)

La seconde mission de l'AGC est de gérer l'orientation et la propulsion du vaisseau.

Le DAP est un système de commande électrique qui permet au pilote de définir une attitude souhaitée sans se préoccuper des RCS. (montrer) Les RCS sont des petits moteurs.  
Le DAP doit calculer quels moteurs allumer, quand et combien de temps. Il doit intégrer les potentiels propulseurs HS (héritage de Gemini) et la répartition de la masse du vaisseau.  

Pour rappel : une force qui passe par le centre de la masse d'un objet provoque une translation. Si cette force est excentrée, elle provoque plutôt une rotation de l'objet autour du centre de la masse.

L'emplacement des RCS reste fixe, mais les configurations et la répartition des masses très variées au cours d'une mission.

Ce problème est si complexe que le DAP représente à lui seul 10% du code de l'AGC.

### Affichage (15s)

Affichage à l'équipage de l'état des système et des paramètres de vol.

### Liaison avec le sol et télémétrie (1min)

L'AGC n’est pas un système entièrement autonome, il intègre en cours de mission des données uploadées depuis le sol.  
Il envoie également des données sur son état au centre de contrôle, ce qui leur permettait d'analyser l'état du vaisseau, mais aussi de visualiser en direct ce que voyait et faisait l'équipage, une sorte de partage d'écran. 


---

# Le système

### Intro Margaret Hamilton

Vous devez connaitre Margaret Hamilton, elle était responsable de l'équipe du Draper Labotory du MIT. C'est elle et son équipe qui ont développé le software de l'AGC.  

L'AGC est un ensemble de mécaniques simples qui produisent ensemble un comportement complexe.  
Le résultat de leurs travaux est un système multiprocessus. 

### Le multiprocessing

Le multiprocessing permet une meilleure gestion de la complexité et une meilleure testabilité des différents programmes.  
À l'époque, il existait deux grandes stratégies pour gérer un système multi-process:  
- le "Cooperative multiprogramming", aka "je peux rendre la main"
- le "Preemptive multiprogramming", aka "ton temps CPU est terminé"  

L'AGC utilisait un mix de ces deux stratégies.

### L'executeur : le light OS

Il n'existait pas d'OS à proprement parler pour gérer ces processus, cette gestion était le rôle de l'executeur.  

Le coeur de l'executer c'est 3 tables avec des adresses fixes :  
- le core set qui contient les processus en cours d'exécution ainsi que leurs priorité. 6 process pour le CM, 7 pour le LM
- le VAC qui contient l'état des processus en cours
- la WAITLIST qui contient les processus programmé et le temps restant avant de les démarrer

Pour administrer ces tables, il y a un ensemble de routines pour démarrer, stopper, programmer, changer la prioriter d'un processus, etc...

### L'executeur : le temps et les IO

Comme je l'ai évoqué avec la WAITLIST, la gestion du temps est importante. On retrouve dans l'AGC plusieurs timers, par exemple :  
- Le TIMER 3 permet de déclencher les jobs programmés dans la waitlist.  
- Le TIMER 4 permet de déclencher des routines de vérification de l'état des systèmes.  

Ces interruptions provoquent des context switch : le processus en cours est interrompu, déchargé et un nouveau processus est chargé à la place.  
Le TIMER 4 provoque à lui seul 8 context switch par seconde.  

### Aparté : Les compteurs

Certains appareils comme la centrale inertielle peuvent générer beaucoup d'I/O. Par exemple l'IMU a une précision de 39 seconde d'arc, une rotation de quelques degrés/seconde sur un seul axe provoque rapidement des centaines voir des milliers d'interruptions.  

Les ingénieurs ont mis en place un hack pour contourner ce problème : le "cycle stealing".  

Pour des opérations I/O visant a incrémenter/décrémenter des compteurs, le hardware envoie des "pulses" dans des registres dédiés du CPU.  
Quand le CPU détecte un de ces pulses, il va "voler" son prochain cycle au processus en cours d'exécution pour aller modifier en mémoire vive le compteur impacté. L'opération reste totalement transparente pour le processus en cours.  

### Exécuteur : Gestion des erreurs

Le dernier rôle de l'exécuteur est la gestion des erreurs, en cas de plantage d'un processus, il existe trois scénarios possibles :  
- P00DOO : le processus n'est pas très important et est stoppé sans redémarrage 
- software restarts : le processus doit être redémarré, s'en suis tout une séquence d'interruption des processus, de néttoyage des tables de l'exécuteur avant de redémarrer les processus
- AGC "fresh start" : arrive si le software restarts échoue, tout est nettoyé jusqu'au hardware, l'AGC est placé dans un état "Idle" et implique des opérations de la part des astronautes

Dans le cas du software restart, les logiques de redémarrage sont stockés dans la mémoire morte : Group table & Restart table  
Pour économiser du temps de calcul sur les processus les plus coûteux, certains d'entre eux peuvent être redémarré au milieu de leur exécution, c'est le rôle de phase table de stocker les paramètres nécessaire à cette reprise.  
La phase table a également un second rôle, stocker le Major mode (MODREG) de l'AGC.  

### Interpréteur

Tout ce que j'ai évoqué jusqu'à maintenant est codé en assembleur.  
Pour permettre de s'abstraire un peu du CPU, l'AGC est doté de l'interpreteur, une autre architecture CPU "logicielle".  

Elle apporte de nouvelles capacités comme les vecteurs ou encore des fonctions arithmétiques et trigonométriques.

Cette surcouche ajoute un coût en ressources CPU, par exemple: SIN = 5.6ms; ACOS = 9.1ms).  

C'est pour cette raison que les processus peuvent mélanger du code assembleur et du code exécuté sur l'interpreteur pour maximiser l'usage des ressources et la performance.  

### Langage de haut niveau

L'interpreteur est également pensé pour être utilisé avec un langage de haut niveau.  
Celui-ci reste une forme d'assembleur, mais avec des instructions de plus haut niveau pour manipuler les types "complexes" de l'interpreteur.  
A l'écran on peut par exemple voir des racines carrés (SQRT), des soustractions (DSU) ou encore des divisions (DDV).  

Enfin, les traitements sont exprimés sous la forme d'expressions qui peuvent être parcourus sous la forme d'arbres.  
Cela a un gros avantage sur la gestion de la mémoire car une simple stack/pile suffit : on ajoute les états intermédiaire, et quand on a besoin d'en récuppére un, il s'agit forcément de l'élément en au de la pile.

---


# Les principaux incidents

Je vais maintenant vous parler des principaux incidents de vol qui ont impliqué l'AGC.

### Apollo 11

Le premier a eu lieu au cours de la mission Apollo 11 : on est à bord du module lunaire, en pleine descente propulsive a environ 33000 pieds au-dessus de la surface (l'altitude à laquelle vol un avion de ligne).  
Tout se déroule bien quand soudain une alarme sonne. 1202, c'est la première d'une série de 4 alarmes au cours de cette descente (3 * 1202 et 1 * 1201).  

Au cours de l'alunissage, l'AGC a 3 grandes missions : la navigation, la propulsion et calculer des solutions de rendez-vous en cas d'abandon. C'est la phase de la mission avec la plus grosse charge de travail.  

Plus tôt dans la descente, la procédure demandait à l'équipage d'actionner un switch qui contrôle le radar de rendez-vous. Une malfonction hardware va alors provoquer un déphasage électrique entre l'AGC et le radar.  

La conséquence est une multiplication du nombre de pulses reçus par l'AGC, environ 15% du temps CPU est alors alloué aux cycle stealing.  
Les processus en cours sont donc ralentis et commencent à mettre trop de temps à être exécutés.  

Les alarmes surviennent au moment où l'AGC tente de démarrer un processus programmé dans la WAITLIST alors qu'il n'y a plus de place disponible dans le CORE SET (1202) ou dans le VAC (1201).  

À chacune de ses alarmes, l'AGC initie une séquence de "software restart" avec succès et reprend sa mission. Si cette séquence avait échoué, Apollo 11 aurait très probablement été un échec et le vaisseau potentiellement perdu.  

### Apollo 14

### Transcript

Le second incident majeur a eu lieu au cours d'Apollo 14.  
Pendant que le LM est en orbite lunaire et prépare sa descente, les équipes à Huston analysent les données et constatent une anomalie : le bit du "abort button" est à 1.  

Après quelques manipulations demandées à l'équipage, il est conclu qu'il n'y a pas de problème logiciel et que le bouton est fautif. On suspecte un déchet de soudure qui flotte dedans et crée des contacts intermittents.  

Si cela se produit au cours de la descente alors la mission sera un échec.  

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
Les ingénieurs qui ont travaillé.e.s sur l'AGC ont été des pionnères et des pionners sur tout un ensemble de problématiques. Leurs solutions ont pu profiter à l'ensemble de notre industrie.  
Cependant, ne voyez pas le programme Apollo comme une étape nécessaire au développement de l'informatique modèrne tel qu'on la connait aujourd'hui. Ces découvertes auraient été faites tôt ou tard. Apollo et l'AGC ont plus été des incubateurs et des accelerateurs pour le développement de ces technologies.  
