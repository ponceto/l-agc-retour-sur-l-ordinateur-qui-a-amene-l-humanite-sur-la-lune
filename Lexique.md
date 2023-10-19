Acronymes et mots techiques : 

| Terme technique           | Acronyme | Prononciation de l'acronyme (en français) | Définition                                                                                                    |
| ---                       | ---      | ---                                       | ---                                                                                                           |
| Apollo Guidance Computer  | AGC      | a-g-c                                     | Ordinateur de bord des capsules (module de commande et module lunaire) Apollo                                 |
| Inertial Measurement Unit | IMU      | i-m-u                                     | Centrale intertielle mesurant les changements d'attitude et les accélérations                                 |
| Digital Autopilote        | DAP      | "dape"                                    | Système de commandes de vol électriques                                                                       |
| Reaction control system   | RCS      | r-c-s                                     | Ensemble de propulseurs qui servent à orienter le vaisseau                                                    |
| Command module            | CM       | "c-m"                                     | Module de commande (seul élément à revenir sur Terre)                                                         |
| Lunar module              | LM       | "lem"                                     | Module lunaire                                                                                                |
| Core set table            | -        | -                                         | Table de 6 (CM) ou 7 (LM) fois 12 mots pour stocker les processus en cours d'exécution                        |
| Vector Accumulator areas  | VAC      | "vaque"                                   | Table de 5 fois 44 mots pour stocker l'état des processus exécutés dans l'interpreteur                        |
| Wait list                 | -        | -                                         | Table contenant les tâches de fond à exécuter dans un futur proche                                            |
| Coupling Data Unit        | CDU      | c-d-u                                     | Unité de convertion analogique->digital pour interfacer l'AGC avec les systèmes hardware                      |
| Cycle stealing            | -        | -                                         | Instruction CPU pour incrémenter/décrémenter des compteurs dans interuption du processus en cours d'exécution |
| Phase table               | -        | -                                         | Table contenant les paramètres pour redémarrer un processus à un état connu, contient également le MODREG     |
| Processeur                | CPU      | c-p-u                                     | -                                                                                                             |
| Display and Keyboard      | DSKY     | "disqui"                                  | Principale interface homme-machine de l'AGC                                                                   |
| Bit du bouton abort       | LETABORT | "let abort"                               | Bit en mémoire permettant d'inhiber une action sur le bouton d'arrêt d'urgence de l'alunissage                |
| Major mode register       | MODREG   | "mode regue"                              | Stocke le mode majeur dans lequel se trouve l'AGC                                                             |
| Porte NON-OU              | NOR      | "nore"                                    | Porte logique donnant 1 si toutes les entrées sont à zéro                                                     |
| Porte NON-ET              | NAND     | "nande"                                   | Porte logique donnant 1 si l'une des entrées est à zéro                                                       |
| Entrée/Sortie             | I/O      | "aïe-o"          |   |
