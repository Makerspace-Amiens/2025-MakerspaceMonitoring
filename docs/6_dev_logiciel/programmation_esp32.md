---
layout: default
title: 🔌Programmation des ESP32 avec Tasmota
parent: 6. Développement logiciel
nav_order: 30
---

## 🔌 6.1 Programmation des ESP32 avec Tasmota

🧠 Cette section décrit comment nous avons préparé les microcontrôleurs **ESP32-C3 (XIAO Seeed Studio)** avec le firmware **Tasmota**, afin de connecter des capteurs, configurer le Wi-Fi, et publier les données via **MQTT**.

---

### 🔧 Microcontrôleur utilisé : XIAO ESP32-C3 (Seeed Studio)

Le microcontrôleur **XIAO ESP32-C3** est compact, économique, doté d’une connectivité Wi-Fi, et parfaitement adapté à l’environnement Tasmota. Il est alimenté via **USB-C**, ce qui facilite la configuration initiale depuis un ordinateur.
<p align="center">
  <img src="https://github.com/user-attachments/assets/4b3f7a12-bde5-4e52-b964-d5abf5f9e2b6" alt="Schéma de câblage ESP32-C3" width="200"/>
</p>
---

### 💻 Installation de Tasmota

Nous avons utilisé le firmware officiel **Tasmota** spécialement compilé pour les ESP32-C3. Il s'agit du fichier :

**`tasmota32c3.factory.bin`**

🔗 Lien de téléchargement direct :
👉 [tasmota32c3.factory.bin (OTA)](https://ota.tasmota.com/tasmota32/release/tasmota32c3.factory.bin)

Ce fichier est une **version d’usine** du firmware Tasmota. Il contient le bootloader et la configuration initiale pour permettre à l’ESP32-C3 de démarrer directement dans un environnement prêt à l’emploi. Ce firmware est indispensable pour un premier flash.

---

#### 1. Effacement de la mémoire flash

Branchez le XIAO ESP32-C3 via USB, puis exécutez dans un terminal :

```bash
python -m esptool --chip esp32c3 --port COMx erase_flash
```

> Remplacez `COMx` par le port série utilisé (ex. `COM3` sous Windows ou `/dev/ttyUSB0` sous Linux).

#### 2. Flash du firmware Tasmota

Installez ensuite `tasmota32c3.factory.bin` :

```bash
python -m esptool --chip esp32c3 --port COMx write_flash -z 0x0 tasmota32c3.factory.bin
```

> 💡 Téléchargez le fichier depuis le lien ci-dessus et placez-le dans le dossier courant, ou indiquez son chemin complet.

---

### 📱 Configuration initiale de Tasmota

Dès que le module redémarre :

#### 1. Connexion au Wi-Fi de Tasmota

Un réseau Wi-Fi temporaire est généré (type `tasmota_XXXXXX`). Connectez-vous depuis un ordinateur ou un smartphone.

#### 2. Configuration du Wi-Fi

L’interface s’ouvre automatiquement (ou via `192.168.4.1`) pour entrer les identifiants du Wi-Fi du MakerSpace.

Une fois connecté, le module rejoint le réseau local et se voit attribuer une adresse IP.

---
<p align="center">
  <img src="https://www.domo-blog.fr/wp-content/uploads/2022/05/sonoff-dual-r3-menu-configuration-tasmota.png" alt="Schéma de câblage ESP32-C3" width="450"/>
</p>
### 📡 Configuration MQTT dans Tasmota

Accédez à l’interface Tasmota via l’IP attribuée, puis allez dans `Configuration > Configure MQTT` et remplissez :

- **Host** : `172.16.4.33` (adresse IP du broker MQTT)
- **Port** : `1883`
- **Client** : `esp32c3-capteur` (nom unique)
- **Topic** : `capteur`
- **User / Password** : *(laisser vide si non requis)*
<p align="center">
  <img src="https://iotdesignpro.com/sites/default/files/inline-images/Configure-MQTT.png" alt="Schéma de câblage ESP32-C3" width="450"/>
</p>
---

### 📎 Affectation des capteurs sur les GPIO

Dans `Configuration > Configure Module`, choisissez **Module Generic (18)**, puis assignez les GPIO aux capteurs connectés.

#### 🔹 AMS2302 (température & humidité)

- Capteur branché sur **GPIO10**
- Type dans Tasmota : **AM2301**

| Fonction    | GPIO   | Remarque                                  |
|-------------|--------|-------------------------------------------|
| Data        | GPIO10 | Un seul fil de données (1 fil + GND + VCC) |

#### 🔹 PMS7003 (particules fines PM1.0 / PM2.5 / PM10)

Ce capteur UART est compatible avec **PMS5003** dans Tasmota :

| Fonction      | GPIO    | Remarque                          |
|---------------|---------|-----------------------------------|
| TX (capteur)  | GPIO20  | → RX de l’ESP32                   |
| RX (capteur)  | GPIO21  | ← TX de l’ESP32                   |

---

### 🧪 Vérification du fonctionnement

Les messages MQTT peuvent être lus via **MQTT Explorer**, ou intégrés dans **OpenHab** ou **Home Assistant**.

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

✅ Grâce à Tasmota, l’ESP32-C3 publie les données des capteurs en temps réel sans écrire de code, ce qui simplifie et fiabilise le déploiement dans le MakerSpace.

