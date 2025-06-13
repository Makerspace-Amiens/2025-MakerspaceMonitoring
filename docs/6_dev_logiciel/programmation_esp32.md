---
layout: default
title: ✅ test pour voir
parent: 6. Développement logiciel
nav_order: 30
---

## 🔌 6.1 Programmation des ESP32 avec Tasmota

🧠 Cette section décrit comment nous avons préparé les microcontrôleurs **ESP32-C3** avec le firmware **Tasmota**, afin de connecter facilement des capteurs, configurer le Wi-Fi, et publier les données via **MQTT**.

---

### 🔧 Microcontrôleur utilisé : ESP32-C3

Nous avons utilisé le **ESP32-C3** proposé par **Seeed Studio**, un microcontrôleur compact, économique, compatible Wi-Fi et supporté par le firmware Tasmota. Il est alimenté via un port **USB-C**, ce qui simplifie son raccordement direct à un ordinateur pour la configuration initiale.

---

### 💻 Installation de Tasmota

Avant d'utiliser Tasmota, nous avons préparé les ESP32-C3 via un PC, avec les étapes suivantes :

#### 1. Effacement de la mémoire flash

Connexion de l'ESP32-C3 via USB, puis exécution de la commande suivante dans un terminal :

```bash
esptool.py --chip esp32c3 erase_flash
```

#### 2. Flash du firmware Tasmota

Après avoir effacé la mémoire, on installe la version de Tasmota adaptée (dans notre cas `tasmota32c3.bin`) :

```bash
esptool.py --chip esp32c3 --baud 460800 write_flash -z 0x0 ~/firmwares/tasmota/tasmota32c3.bin
```

> 💡 Remplace le chemin `~/firmwares/tasmota/tasmota32c3.bin` par l’emplacement exact du fichier sur ton système.

---

### 📱 Configuration initiale de Tasmota

Une fois le flash terminé et l’ESP32 redémarré :

#### 1. Connexion au Wi-Fi de Tasmota

Le module crée un point d’accès Wi-Fi temporaire, du type `tasmota_XXXXXX`. On s’y connecte depuis un smartphone ou un ordinateur.

#### 2. Configuration du Wi-Fi

Une interface web s’ouvre automatiquement (ou est accessible via `192.168.4.1`) pour entrer les identifiants du réseau Wi-Fi du MakerSpace.

Une fois connecté, Tasmota rejoint le réseau et obtient une adresse IP locale.

---

### 📡 Configuration MQTT dans Tasmota

L’interface web Tasmota est ensuite accessible via l’adresse IP attribuée. Dans `Configuration > Configure MQTT`, nous avons saisi :

- **Host** : `192.168.1.10` (adresse IP du broker MQTT)
- **Port** : `1883`
- **Client** : `esp32c3-capteur-co2` (nom unique)
- **Topic** : `makerspace/capteur-co2`
- **User / Password** : *(optionnel selon configuration du broker)*

---

### 📎 Affectation des capteurs aux pins

Chaque capteur est branché sur des **GPIO** spécifiques. Dans `Configuration > Configure Module`, nous avons sélectionné le **Module Generic (18)**, puis affecté les GPIO aux capteurs.

#### Exemple : capteur de CO₂ MH-Z19B

| Fonction         | GPIO   | Remarque                         |
|------------------|--------|----------------------------------|
| Sensor TX (RxD)  | GPIO20 | RX du capteur → TX de l’ESP32   |
| Sensor RX (TxD)  | GPIO21 | TX du capteur → RX de l’ESP32   |

Une fois sauvegardé, Tasmota reconnaît automatiquement le capteur et commence à publier les données sur le **topic MQTT** défini.

---

### 🧪 Vérification de fonctionnement

Les messages envoyés par Tasmota peuvent être visualisés via un outil comme **MQTT Explorer**, ou directement dans **OpenHab / Home Assistant**.

#### Exemple de message publié par le capteur MH-Z19B :

```json
{
  "Time": "2025-06-13T10:25:43",
  "MHZ19B": {
    "CarbonDioxide": 647
  }
}
```
