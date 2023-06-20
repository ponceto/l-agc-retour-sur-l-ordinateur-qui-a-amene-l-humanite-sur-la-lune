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
La course à la Lune est un bon objectif, car elle nécessite des avancées techniques et technologiques importantes, même pour les Soviétiques, ce qui gommerait leur avance.


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

### L'échelle (20s)

Le schéma n'est pas à l'échelle, la distance Terre-Lune est de 400 000 km. La précision nécessaire pour naviguer est donc très importante.  

La mission première de l'AGC est donc la navigation.  

### C'est où le haut ? (1m)

La première question est : comment s'orienter ? Sur Terre la gravité définit naturellement le bas et le haut et est un référentiel adapté à beaucoup de situations du quotidien.  
Dans l'espace, cette force est beaucoup moins adaptée à cause de l'apesanteur et parce que le vecteur gravité n'est pas fixe au cours d'une orbite.   
On utilise le système Terre-Lune ainsi que des étoiles comme points de références.  
L'AGC intègre 5 référentiels adaptés aux différentes phases d'une mission lunaire.

### Où suis-je ? (1m)

Ensuite il faut savoir où l'on se trouve. Les systèmes inertiels n'étant pas parfaits, il faut pouvoir réaligner la centrale en vol.  
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
Il envoie également des données sur son état au centre de contrôle, ce qui leur permettait d'analyser l'état du vaisseau, mais aussi de visualiser en direct ce que voyait et faisait l'équipage. 


---

# Le système

### Intro Margaret Hamilton

Vous devez connaitre Margaret Hamilton, elle était responsable de l'équipe du Draper Labotory du MIT. C'est elle et son équipe qui ont développé le software de l'AGC.  

Le résultat de leurs traveux un système multiprocessus. Cela permet une meilleure gestion de la complexité et une meilleure testabilité des différents programmes.

### Le multiprocessing

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


---

# Conclusion