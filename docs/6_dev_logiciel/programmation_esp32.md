---
layout: default
title: ✅ test pour voir
parent: 6. Développement logiciel
nav_order: 30
---

## 🔌 6.1 Programmation des ESP32 avec Tasmota

🧠 Cette section décrit comment nous avons préparé les microcontrôleurs **ESP32-C3 (XIAO Seeed Studio)** avec le firmware **Tasmota**, afin de connecter des capteurs, configurer le Wi-Fi, et publier les données via **MQTT**.

---

### 🔧 Microcontrôleur utilisé : XIAO ESP32-C3 (Seeed Studio)

Le microcontrôleur **XIAO ESP32-C3** est compact, économique, doté d’une connectivité Wi-Fi, et parfaitement adapté à l’environnement Tasmota. Il est alimenté via **USB-C**, ce qui facilite la configuration initiale depuis un ordinateur.

---

### 💻 Installation de Tasmota

Nous avons utilisé le firmware officiel **Tasmota** spécialement compilé pour les ESP32-C3. Il s'agit du fichier :

**`tasmota32c3factory.bin`**

🔗 Lien de téléchargement officiel :
👉 https://github.com/arendst/Tasmota/releases/latest

Ce fichier est une **version d’usine** du firmware Tasmota : il contient le bootloader et la configuration initiale pour permettre à l’ESP32-C3 de démarrer directement dans un environnement prêt à l’emploi. Il est indispensable pour un premier flash.

---

#### 1. Effacement de la mémoire flash

Branchez le XIAO ESP32-C3 via USB, puis exécutez dans un terminal :

```bash
python -m esptool --chip esp32c3 --port COMx erase_flash
```

> Remplacez `COMx` par le port série utilisé (ex. `COM3` sous Windows ou `/dev/ttyUSB0` sous Linux).

#### 2. Flash du firmware Tasmota

Installez ensuite `tasmota32c3factory.bin` :

```bash
python -m esptool --chip esp32c3 --port COMx write_flash -z 0x0 tasmota32c3factory.bin
```

> 💡 Assurez-vous que le fichier `.bin` se trouve dans le répertoire courant, ou indiquez le chemin complet.

---

### 📱 Configuration initiale de Tasmota

Dès que le module redémarre :

#### 1. Connexion au Wi-Fi de Tasmota

Un réseau Wi-Fi temporaire est généré (type `tasmota_XXXXXX`). Connectez-vous depuis un ordinateur ou un smartphone.

#### 2. Configuration du Wi-Fi

L’interface s’ouvre automatiquement (ou via `192.168.4.1`) pour entrer les identifiants du Wi-Fi du MakerSpace.

Une fois connecté, le module rejoint le réseau local et se voit attribuer une adresse IP.

---

### 📡 Configuration MQTT dans Tasmota

Accédez à l’interface Tasmota via l’IP attribuée, puis allez dans `Configuration > Configure MQTT` et remplissez :

- **Host** : `172.16.4.33` (adresse IP du broker MQTT)
- **Port** : `1883`
- **Client** : `esp32c3-capteur` (nom unique)
- **Topic** : `capteur`
- **User / Password** : *(laisser vide si non requis)*

---

### 📎 Affectation des capteurs sur les GPIO

Dans `Configuration > Configure Module`, choisissez **Module Generic (18)**, puis assignez les GPIO aux capteurs connectés.

#### 🔹 AMS2302 (capteur d’humidité/température)

Ce capteur est branché sur **GPIO10**. Il est configuré comme un **AM2301** (équivalent supporté par Tasmota).

- **GPIO10** : AM2301

#### 🔹 PMS7003 (capteur particules fines)

Ce capteur communique en UART et est compatible avec la configuration **PMS5003** dans Tasmota. Il est branché ainsi :

- **GPIO20** : PMS5003 TX (capteur → RX du module)
- **GPIO21** : PMS5003 RX (capteur ← TX du module)

Une fois la configuration sauvegardée, Tasmota détecte les capteurs et publie automatiquement les données sur le topic MQTT.

---

### 🧪 Vérification du fonctionnement

Les messages MQTT peuvent être lus via **MQTT Explorer** ou directement intégrés dans **OpenHab** ou **Home Assistant**.

#### Exemple de message JSON publié :

```json
{
  "Time": "2025-06-13T12:07:23",
  "AM2301": {
    "Temperature": 24.7,
    "Humidity": 49.5
  },
  "PMS5003": {
    "PM1.0": 6,
    "PM2.5": 10,
    "PM10": 14
  }
}
```

---

✅ Grâce à Tasmota, l’ESP32-C3 peut publier des données en temps réel sans aucune ligne de code personnalisée, ce qui facilite le déploiement rapide dans un environnement MakerSpace.
