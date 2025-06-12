---
layout: default
title: 🧰 Création de PCB
parent: 4. Conception des capteurs connectés
nav_order: 21
---

# 🧰 Création de PCB (Carte électronique)

Une carte de circuit imprimé, communément appelée PCB (Printed Circuit Board), est un support physique essentiel utilisé dans la majorité des dispositifs électroniques modernes. Elle permet à la fois de connecter électriquement et de supporter mécaniquement les composants électroniques.
Autrement dit, c’est l’ossature de tout appareil électronique, servant à organiser, structurer, interconnecter et fixer tous les éléments nécessaires au fonctionnement du circuit. Une fois que les composants électroniques sont à notre disposition, on va pouvoir souder ceux-ci sur notre PCB pour les connecter et qu'ils puissent également intéragir avec le microcontrôleur et les autres composants.

Dans le cadre de notre projet, nous avons décider de créer nos propre PCB grâce à un logiciel très connu : KiCad EDA

![image](https://github.com/user-attachments/assets/7ef722a1-f944-400f-97f6-8a8b3b7a8b7c)


KiCad EDA (pour KiCad Electronic Design Automation) est une suite logicielle libre et open-source destinée à la conception de circuits électroniques et de cartes de circuits imprimés (PCB).
Elle permet à un utilisateur de créer un schéma électronique, de le simuler, puis de concevoir la carte PCB associée, prête pour la fabrication.
KiCad regroupe 3 grandes parties sur le logiciel:

                               -Eeschema (Éditeur de schémas), on peut y retrouver:
                                     - Création de schémas électroniques complets avec symboles et empreintes
                                     - Ajout de symboles, liaisons, alimentations (par exemple 3,3V ou 5V), annotations automatiques
                                     - Vérification des règles électriques (ERC)

![image](https://github.com/user-attachments/assets/20b4ff63-13a8-4bab-b177-bb10b2184054)


                                           -Pcbnew (Éditeur de PCB), dans cette section on manipulera:
                                                 - Conception de la carte PCB à partir du schéma
                                                 - Routage automatique ou manuel des pistes
                                                 - Gestion des vias, zones de cuivre, plan de masse
                                                 - Affichage 2D/3D du PCB
                                                 

![image](https://github.com/user-attachments/assets/fc7a95e4-410d-49bc-97d9-62d41236f1b3)


                                          -Footprint editeur (Editeur d'empreinte), c'est ici que l'on va:
                                                 - Créer des empreintes personnalisées
                                                 - Modifier des empreintes existants
                                                 - Ajuster les pads, trous
                                                 - Visualiser en 2D et 3D l’empreinte
                                                 

![image](https://github.com/user-attachments/assets/79b3a017-c8a2-49ea-a8dc-4ace2132ba73)

Pour commencer notre création de PCB, il fallait définir quels composants éléctroniques nous voulions intégrer sur notre carte électronique. Il était necessaire aussi de savoir quel microcontôleur utiliser. Nous sommes donc partis sur le capteur de température et d'humidité (AMS2302) et le capteur de qualité de l'air (PMS7003). En ce qui concerne le microcontrôleur, nous nous sommes tournés vers le Xiao, designé et fabriqué en grande partie par la société Seeed Studio.

![image](https://github.com/user-attachments/assets/071d90f7-b076-423b-94d7-6c04e3c93969)

Deuxiemement sur KiCad, nous avons creer un nouveau projet et mis tous les composants électroniques que nous voulions dans Eeschema ce qui constitue la première étape.

![image](https://github.com/user-attachments/assets/75a7c99f-ce8c-4ca8-873c-44a0437435e1)<img src="images/mon-schema.png" width="500"/>


Ici on peut voir que le XIAO a été ajouté au centre grâce à une bibliothèque que l'on a importé dans le logiciel ainsi que son empreinte. Le AMS2302 était déjà installé dans Kicad, on a donc pu l'integrer assez facilement dans l'éditeur de schémas. Pour le PMS7003, nous avons opté pour un connecteur 02x05 car le capteur a le meme nombre de broches, de lignes et de colomnes. On viendra alors souder le capteur sur le connecteur. Des résistances ont été ajoutéescar elle étaient essentielles dans le branchements des capteurs ainsi qu'une LED pour avoir un visuel sur l'état de la carte (allumée ou éteinte).

![image](https://github.com/user-attachments/assets/4456a7ab-553d-45f7-8002-7f202aa59427)

C'est dans cette section que l'on va assigner une empreinte a un composant électronique. 
Une empreinte est une description physique et graphique d’un composant électronique, conçue pour le placement sur un circuit imprimé (PCB). Elle décrit la forme, la taille et la position des zones de soudure (pastilles), les trous, et parfois d’autres éléments mécaniques.






---
