# Le contexte historique (2m30)

S'il y a un événement pour marquer l'aventure lunaire, c'est sans nul doute de discours de John Fitzgerald Kennedy donné le 25/05/1961 devant le Congrès américain. Il fixe un objectif majeur pour la nation : amener un Américain sur la Lune avant la fin de la décennie.  
Pour bien comprendre cette décision, il faut se rappeler que nous sommes en pleine guerre froide, et que les États-Unis accusent un important retard sur les Soviétiques sur tout ce qui touche au spatial.

Petit rappel des événements : 
- le 04/10/1957 : Spoutnik (URSS) est le 1er satellite artificiel en orbite, c'est un véritable choque pour les Américains
- à cette époque, les États-Unis n'ont même pas de programme spatial national, pour y remédier, il faut attendre la création de la NASA le 29/07/1958 
- le 07/10/1959, nouveau coup de massue : la sonde soviétique LUNA 3 prend la 1er photographie de la face cachée de la Lune
- le coup de grâce arrive le 12/04/1961 : Youri Gagarine (URSS) est le 1er homme dans l'espace, il réalise une orbite complète autour de la Terre
- Seulement 3 semaines après Gagarine et 20 jours avant le discours de JFK, le 05/05/1961, Alan Shepard (USA) est le 1er Américain dans l'espace. **Mais** il s'agit d'un vol suborbital (aka: on l'a juste envoyé assez haut pour qu'il soit techniquement dans l'espace).
- pour avoir un Américain en orbite terrestre, il faut attendre le vol de John Glenn (USA) le 20/02/1962 

Les Américains sont en retard, et pour faire oublier ce retard ils ont besoin d'un exploit.  
La course à la Lune est un bon objectif, car elle nécessite des avancées techniques et technologiques importantes, même pour les Soviétiques. 


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
Dans l'espace, cette force est beaucoup moins adaptée à cause de l'apesanteur et parce que le vecteur gravité n'est pas fixe au cours d'une orbite. Et toutes les phases de vol ne se déroulent pas en orbite.  
On utilise des étoiles comme points de références.  
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

Pour rappel : une force qui passe par le centre de la masse d'un objet provoque une translation. Si cette force est excentrée, elle provoque plutôt une rotation de l'objet.

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

Ils ont développé un système multiprocessus pour une meilleure gestion de la complexité et une meilleure testabilité.

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
- la waitlist qui contient les processus programmé et le temps restant avant de les démarrer

Pour administrer ces tables, il y a un ensemble de routines pour démarrer, stopper, programmer, changer la prioriter d'un processus, etc...

### L'executeur : le temps et les IO




---

# Les principaux incidents


---

# Conclusion