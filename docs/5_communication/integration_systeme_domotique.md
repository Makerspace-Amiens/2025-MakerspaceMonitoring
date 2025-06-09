---
layout: default
title: 🔗 Intégration des capteurs au système domotique
parent: 5. Communication et interconnexion
nav_order: 26
---

# 🔗 Intégration des capteurs au système domotique

Après avoir établi la communication via MQTT, la prochaine étape consiste à intégrer de manière efficace les données collectées par les capteurs dans la plateforme domotique choisie, à savoir OpenHab. Cette intégration permet l'utilisation des mesures dans des scénarios domotiques, des tableaux de bord ou des alertes.

#### Configuration du broker MQTT dans OpenHab

La configuration du broker MQTT dans OpenHab se fait nativement en installant l'extension "MQTT Binding". Dans notre projet, nous avons configuré OpenHab pour se connecter au broker Mosquitto installé localement sur le NUC. Pour cela, un "MQTT Broker Thing" a été ajouté dans OpenHab avec les paramètres suivants : 
- Adresse du broker : `adresse IP du NUC`
- Port : `8080`

#### Déclaration des capteurs (Things)

Cette étape établit la connexion entre OpenHab et le flux de données MQTT.

Chaque capteur est représenté dans OpenHab par un **Thing** de type MQTT. Chaque Thing regroupe un ou plusieurs Channels, correspondant à une donnée mesurée. 

Par exemple, pour un capteur de température dans le PrinterLAB, un Thing est défini avec un Channel lié au topic : `makerspace/printerlab/temperature`. 

Le Channel est configuré pour recevoir un message JSON, et un "transformateur" peut être utilisé pour extraire la donnée pertinente, par exemple : `JSONPATH:$.valeur`

#### Liaison avec les Items

Ensuite, les Channels sont liés à des Items, représentant les données dans l'interface d'OpenHab. Chaque Item peut être utilisé pour afficher une valeur sur un tableau de bord, lancer une automatisation ou déclencher une alerte.

Une fois les Items configurés, les données des capteurs sont disponibles dans l'interface OpenHab sous forme de graphiques, jauges ou valeurs numériques simples.

---


