---
layout: default
nav_order: 4
title: Études et choix techniques
---

# Études et choix techniques

Durant le projet, nous avons fait beaucoup de choix techniques après une étude avancées de solutions déjà existantes. Dans cette partie nous détaillerons les alternatives que nous avons trouvé à tous les niveaux ainsi que la décision finale de chaque outil.

## Cahier des charges

Avant de commencer à se lancer dans la recherche de logiciel et de capteur il est important de savoir comment notre projet va fonctionner en établissant notre cahier des charges. Un élément essentiel à sa création et de visualiser le chemin de l'information.

![Image_NUC](images/chemin_info.png)

Un ensemble de capteur sera installé dans les salles pour collecter des informatinos telles que la température et l'humidité. Une fois la donnée collectée il faudra l'envoyer à un serveur qui traitera l'information à l'aide d'une distribution de domotique, pour l'installation de la distribution OpenHab [**Cliquez ici**](config_Mini_PC.md). Enfin on choisit si on veut afficher cette information ou si on veut en faire une action dans le makerspace, par exemple baisser le chauffage si il fait trop chaud.
Les composants seront interconnectés à l'aide du wifi du Makerspace qui nous permet de diffuser nos données dans tout l'étage.
