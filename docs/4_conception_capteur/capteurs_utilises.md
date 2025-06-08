---
layout: default
title: 🌡️ Types de capteurs utilisés
parent: 4. Conception des capteurs connectés
nav_order: 19
---

# 🌡️ Types de capteurs utilisés
Pour pouvoir récupérer des données, nous avons besoin de capteurs, car ce sont eux qui font le lien avec le monde réel. Dans le cadre de notre projet, nous avons choisi deux capteurs pour mesurer trois variables :

                                        -La température
                                        -L'humidité
                                        -La qualité de l'air (taux de particules fines dans l'air)

Pour mesurer la température, nous avons opté pour le DHT22 :
Le DHT22, aussi connu sous la référence AMS2302, est un capteur numérique qui permet de mesurer la température et l'humidité relative de l'air. Il est largement utilisé dans les projets électroniques grâce à sa facilité d'utilisation, sa double fonction (température et humidité) et sa bonne précision pour les projets éducatifs.
# DHT22 (AMS2302)
![image](https://github.com/user-attachments/assets/db738650-507a-4e5f-b6a2-ff1a8c0256c4)



Pour mesurer la qualité de l'air, nous nous sommes orientés vers le PMS7003 :
Le PMS7003 est un capteur de particules fines. Il permet de mesurer la concentration de particules en suspension dans l'air, telles que les PM1.0, PM2.5 et PM10, qui sont des indicateurs importants de la pollution atmosphérique. Ce capteur est souvent utilisé dans les projets de surveillance de la qualité de l'air. Son principal avantage est sa capacité à mesurer trois tailles de particules fines, ce qui en fait l’un des capteurs les plus utilisés dans tous types de projets.
# PMS7003
![image](https://github.com/user-attachments/assets/3299da7d-7bd6-4bfc-96af-cdd59c4fb10c)

Une fois les capteurs choisi, nous devons les souder sur une carte éléctronique.
Une carte électronique est un support rigide ou souple sur lequel sont montés et interconnectés des composants électroniques (comme des résistances, des condensateurs, des microcontrôleurs ou des capteurs). Elle permet de réaliser des circuits électriques complexes pour traiter, contrôler ou transmettre des signaux électriques dans un appareil ou un système.
Une fois que les capteurs ont convertis les donées physiques en signaux électriques, la carte va pouvoir traiter les informations que nous souhaitons analyser.



---
