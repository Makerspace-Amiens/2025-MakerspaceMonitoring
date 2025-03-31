---
layout: home
nav_order: 1
title: Configuration sur Tasmotta
---

# Les capteurs

Les capteurs sont un élément essentiel de notre système, aucune donnée ne peut être collectée et toute action ou affichage devient impossible. Il est alors important de comprendre l'utilité des capteurs, lesquels choisir et comment les utiliser.

## L'utilité des capteurs

Tout d'abord un capteur n'est pas magique, si vous posez une sonde de température dans votre chambre vous n'aurez aucune donnée qui sortira. Un capteur est un processus qui transforme un phénomène physico-chimique en une grandeur numérique électrique. Cela signifie que le phénomène peut être représenté et transporté dans de systèmes informatiques. Pour extraire la donnée de nos capteurs il faudra aussi lui donner un code qui lui servira de traduction de notre demande. Imaginez simplement que votre code dit au capteur (de température dans notre exemple) "Bonjour j'aurai besoin que tu me donnes la température actuelle de la pièce et que tu actualises l'information toutes les 5 secondes". 

![Image_NUC](images/explaincaptor.png)


## Tasmota : Une Alternative Libre pour vos Objets Connectés

![Illustration vectorielle colorée avec un fond blanc, montrant un atelier équipé pour un projet de conception mécanique, électronique et informatique](images/tasmotta.svg)

## Qu'est-ce que Tasmota ?

Tasmota est un **logiciel gratuit et open-source** qui permet de contrôler certains objets connectés, comme des **ampoules, prises intelligentes et capteurs**, sans dépendre d’Internet ou d’une application du fabricant.  
Il remplace le programme d’origine des appareils utilisant une puce **ESP8266 ou ESP32**, offrant ainsi **plus de liberté, de confidentialité et de sécurité**.

## Pourquoi utiliser Tasmota ?

- **Contrôle local** : Vos appareils fonctionnent sans connexion à un serveur externe, ce qui améliore la **sécurité et la confidentialité**.
- **Flexibilité** : Compatible avec **Home Assistant, MQTT, Domoticz**, et bien d’autres solutions domotiques.
- **Indépendance** : Évite la dépendance aux applications et serveurs propriétaires, qui peuvent être fermés ou collecter vos données.
- **Personnalisation avancée** : Permet d’adapter le comportement des appareils selon vos besoins.

## Utiliser Tasmota avec openHAB

Tasmota est entièrement **compatible avec openHAB**, une plateforme domotique open-source qui centralise et automatise la gestion de votre maison intelligente.

### Intégration avec notre projet

Dans notre projet, nous utilisons un **ESP32** sur lequel nous **installons le firmware Tasmota**. Ce microcontrôleur est connecté à un **capteur AM2302**, un capteur de **température et d'humidité de précision**. Une fois le firmware Tasmota installé, l’ESP32 peut récupérer les données mesurées par l’AM2302 et les transmettre via **MQTT** à un broker, qui les relaie ensuite à **openHAB** pour affichage et exploitation.

### Schéma de communication

📡 **Capteur (AM2302) → ESP32 (Firmware Tasmota) → MQTT Broker → openHAB**

1. **Le capteur AM2302 mesure la température et l'humidité** avec précision.
2. **L’ESP32, avec le firmware Tasmota installé, récupère ces données** et les envoie au broker MQTT.
3. **Le broker MQTT transmet les données à openHAB**, qui les affiche et permet d’automatiser des actions.

Avec **Tasmota installé sur ESP32 et openHAB**, nous avons une solution **locale, sécurisée et personnalisable** pour gérer nos capteurs et automatiser notre environnement connecté ! 🚀

---
