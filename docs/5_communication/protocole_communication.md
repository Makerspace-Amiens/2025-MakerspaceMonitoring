---
layout: default
title: 📡 Protocoles de communication
parent: 5. Communication et interconnexion
nav_order: 23
---

# 📡 Protocoles de communication

Dans le cadre de notre projet de domotique au MakerSpace, nous avons mis en place une communication entre les différents composants du système en utilisant une architecture distribuée basée sur des protocoles standards adaptés à l'Internet des Objets (IoT). Le choix de ces protocoles a été guidé par des critères tels que la fiabilité, la légèreté, la compatibilité avec l'ESP32 et la nécessité d'une communication en temps réel entre les capteurs et la plateforme domotique.

#### Wi-Fi

En exploitant la connectivité Wi-Fi intégrée du microcontrôleur ESP32, nous avons opté pour ce protocole afin de connecter les capteurs au réseau local du MakerSpace. Le Wi-Fi offre une couverture adéquate pour l'ensemble des locaux, ainsi qu'une vitesse de transmission adaptée à l'envoi régulier des données des capteurs.

En tirant parti du réseau Wi-Fi interne du MakerSpace, nous avons pu connecter tous les capteurs à ce réseau et héberger le serveur domotique (OpenHab) ainsi que le broker MQTT (Mosquitto) sur un Intel NUC connecté à ce même réseau.

Chaque ESP32 se connecte automatiquement au réseau dès sa mise en marche, simplifiant ainsi le déploiement et la maintenance des dispositifs.

#### MQTT

Le protocole MQTT (Message Queuing Telemetry Transport) occupe une place centrale dans notre système de communication. Léger et basé sur le modèle publish/subscribe, il convient parfaitement aux objets connectés.

Nous avons déployé un broker MQTT Mosquitto sur un NUC local (Intel NUC), qui héberge également le serveur OpenHab. Les capteurs ESP32 publient leurs données sur des topics spécifiques (par exemple : `makerspace/salle1/temperature`) et OpenHab les utilise pour les traiter, les stocker ou les afficher.

Les capteurs envoient des messages au format JSON, un format léger, structuré et largement pris en charge. Cette méthode permet de transmettre diverses valeurs ou métadonnées dans un unique message, ce qui facilite les évolutions futures.

Exemple de message publié :
```json
{
  "valeur": 23.5,
  "unite": "°C",
  "timestamp": "2025-06-08T15:42:10Z"
}
```

---
