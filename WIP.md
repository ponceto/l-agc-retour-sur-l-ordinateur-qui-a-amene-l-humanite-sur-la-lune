
### Apollo 14

### Transcript

Le second incident majeur a eu lieu au cours d'Apollo 14. Nous somme de nouveau à bord du LM mais cette fois-ci en orbite lunaire.  
Pendant que les astronautes préparent le LM pour la descente, les équipes à Huston analysent les données et constatent une anomalie : le bit du "abort button" est à 1.  

Après quelques manipulations demandées à l'équipage, il est conclu que le bouton est fautif. On suspecte un débrit de soudure qui flotte dedans et crée des contacts intermittents.  

Si cela se produit au cours de la descente alors la mission sera un échec. En quelques heures, les ingénieurs vont fournir une solution de contournement.  

### EDIT 1

Par défaut, le bouton est inhibé par un simple bit en mémoire vive, celui-ci est modifié au moment de l'allumage du moteur de sorte à rendre le bouton actif.  
Modifier le programme n'est pas possible puisqu'il est inscrit dans la CORE ROPE.  
Il est par contre possible de le désactiver via quelques instructions sur le DSKY, mais le temps de réaliser cette manipulation, un contact peut être détecté.  

En cas de contact, on effectue deux vérifications avant d'interompre la descente :  

- Le bouton est-il actif ? Il s'agit du bit que l'on souhaite modifier.  
- Est-on déjà entrain d'abandonner l'alunissage ? Pour se faire on va lire le major mode inscrit dans le MODREG.  

Le but va donc être de faire croire à l'AGC qu'il est déjà dans une logique d'abandon le temps de la modification du bit.  

Le hack repose sur un détail de design de l'AGC : le major mode inscrit dans le MODEREG n'est pas nécessairement le major mode réellement executé par l'ordinateur.  

Les astronautes, par le biais du DSKY, vont donc aller modifier cette valeur et y inscrire 71 (major mode d'abandon) avant le démarrage du moteur. Ainsi en cas de contact, la seconde vérification de la routine va empêcher l'abandon.  
Une fois le moteur démarré, les astronautes vont modifier le bit de sorte à désactiver le bouton, puis ils vont réinscrire le programme d'origine dans le MODREG : 63.

En cas de nécessité abort, les astronautes pouvaient toujours démarrer manuellement le programme d'abandon : VERB 37 ENTER 71 ENTER
