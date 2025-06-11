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

![image](https://github.com/user-attachments/assets/bc8a4dfe-665c-484f-b4cf-441f8c8ec6a5)

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

---
