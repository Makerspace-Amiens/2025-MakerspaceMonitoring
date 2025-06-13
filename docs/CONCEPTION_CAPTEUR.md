---
layout: home
title: 5. 🌡️ Conception des capteurs connectés
nav_order: 5
---

# 🧠 Choix du microcontrôleur (ESP32)

## ⚙️ Le microcontroleur XIAO
Le microcontrôleur XIAO est une petite carte électronique très compacte et puissante, idéale pour les projets électroniques et embarqués. Il est basé sur un microcontrôleur ARM Cortex-M0+ 32 bits, ce qui lui confère une bonne performance tout en consommant peu d’énergie.
Sa taille réduite permet de l’intégrer facilement dans des espaces restreints, ce qui est un avantage pour les projets nécessitant un design compact. Malgré sa petite taille, le XIAO offre plusieurs entrées, sorties numériques et analogiques, ainsi que des interfaces de communication comme le UART, I2C et SPI, qui facilitent la connexion avec différents capteurs et modules.
Sa simplicité d’utilisation en fait un choix populaire pour des projets allant de la domotique à la robotique en passant par la surveillance environnementale.

Pour que le microcontrôleur XIAO puisse récupérer et traiter des informations, il est nécessaire de connecter nos capteurs qui mesurent les données sur notre microcontrôleur.
La connectique entre les capteurs et le XIAO permet donc d’établir un lien physique et électrique, indispensable pour que le microcontrôleur puisse recevoir ces signaux. Sans cette connexion, le XIAO ne pourrait ni détecter ni analyser les données mesurées par les capteurs.
# Microcontroleur XIAO

![image](https://github.com/user-attachments/assets/e10235d8-88dd-4ab8-8c51-6c009fc1575c)

---

# 🌡️ Types de capteurs utilisés
Pour pouvoir récupérer des données, nous avons besoin de capteurs, car ce sont eux qui font le lien avec le monde réel. Dans le cadre de notre projet, nous avons choisi deux capteurs pour mesurer trois variables :

                                        -La température
                                        -L'humidité
                                        -La qualité de l'air (taux de particules fines dans l'air)

Pour mesurer la température, nous avons opté pour le DHT22 :
Le DHT22, aussi connu sous la référence AMS2302, est un capteur numérique qui permet de mesurer la température et l'humidité relative de l'air. Il est largement utilisé dans les projets électroniques grâce à sa facilité d'utilisation, sa double fonction (température et humidité) et sa bonne précision pour les projets éducatifs.
## DHT22 (AMS2302)
![image](https://github.com/user-attachments/assets/db738650-507a-4e5f-b6a2-ff1a8c0256c4)



Pour mesurer la qualité de l'air, nous nous sommes orientés vers le PMS7003 :
Le PMS7003 est un capteur de particules fines. Il permet de mesurer la concentration de particules en suspension dans l'air, telles que les PM1.0, PM2.5 et PM10, qui sont des indicateurs importants de la pollution atmosphérique. Ce capteur est souvent utilisé dans les projets de surveillance de la qualité de l'air. Son principal avantage est sa capacité à mesurer trois tailles de particules fines, ce qui en fait l’un des capteurs les plus utilisés dans tous types de projets.
## PMS7003
![image](https://github.com/user-attachments/assets/3299da7d-7bd6-4bfc-96af-cdd59c4fb10c)

Une fois les capteurs choisi, nous devons les souder sur une carte éléctronique.
Une carte électronique est un support rigide ou souple sur lequel sont montés et interconnectés des composants électroniques (comme des résistances, des condensateurs, des microcontrôleurs ou des capteurs). Elle permet de réaliser des circuits électriques complexes pour traiter, contrôler ou transmettre des signaux électriques dans un appareil ou un système.
Une fois que les capteurs ont convertis les donées physiques en signaux électriques, la carte va pouvoir traiter les informations que nous souhaitons analyser.

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


Une fois les composants placés avec leurs empreintes, il faut maintenant faire les liens entre les composants. C'est l'étape du routage. Le routage (ou routing en anglais) est l'étape de conception dans laquelle on dessine les pistes de cuivre qui vont relier les broches des composants électroniques selon le schéma électrique que l’on a défini auparavant.

Il s’agit de transformer un schéma logique (schéma électrique) en un schéma physique (circuit imprimé) fonctionnel, où les connexions ne sont plus symboliques mais bien géométriquement définies sur la carte.

Nous sommes donc passé sur la partie PCB Editor, une fois la partie Eeschéma terminé.

![image](https://github.com/user-attachments/assets/0dbb77e8-6e0e-4c66-9865-f2d269a63e35)

Ici, on peut apercevoir que l'étape du routage a bienété réaliséet que le plan de masse (contour rouge autour de la carte) a bien été ajouté.
Le plan de masse est une grande surface de cuivre connectée au GND (masse) de ton circuit. Il sert à réduire les interférences électromagnétiques et à garantir un bon retour de courant.
Il améliore aussi la stabilité des tensions et facilite le routage des masses. On l'étend souvent sur toute une couche de la PCB (surtout pour les cartes à 2 ou 4 couches).

KiCad est aujourd’hui l’un des logiciels de conception de PCB les plus complets et accessibles. Entièrement open source, il offre une alternative sérieuse aux logiciels propriétaires tout en restant gratuit, ce qui en fait un outil très prisé aussi bien par les étudiants que par les professionnels de l’électronique.
Grâce à ses modules bien structurés – comme Eeschema pour la création des schémas électriques et Pcbnew pour la conception du circuit imprimé – KiCad permet de couvrir toutes les étapes d’un projet électronique. L'utilisateur peut ainsi passer de l'idée à un design prêt à être fabriqué, avec une grande précision.

Le logiciel permet aussi une personnalisation poussée des empreintes, la gestion multi-feuilles pour les projets complexes, la création de plans de masse, le contrôle des règles de design (DRC), ainsi qu'une visualisation 3D du circuit pour anticiper l'encombrement physique et la disposition des composants.

KiCad est également soutenu par une communauté active et une documentation abondante, ce qui facilite l’apprentissage et la résolution de problèmes. Son développement régulier permet l’ajout constant de nouvelles fonctionnalités, rendant l’outil toujours plus performant.

En somme, KiCad se révèle être un environnement de développement fiable et robuste pour la conception de circuits imprimés, alliant flexibilité, puissance et accessibilité à tous les niveaux.

---
