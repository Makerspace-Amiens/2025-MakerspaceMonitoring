---
layout: default
title: ⚙️ Configuration de la solution domotique avec OpenHab
parent: 6. Développement logiciel
nav_order: 29
---

## ⚙️ 6.2 Configuration de la solution domotique avec OpenHab

🧠 Nous avons utilisé **OpenHab** comme plateforme domotique pour centraliser les données des capteurs Tasmota et mettre en place des automatisations.

> Cette partie suppose que vous avez **déjà installé OpenHab sur le NUC** à l’aide de Docker, selon le tutoriel d’installation fourni précédemment.

---

### 🧱 Architecture

- **Microcontrôleurs** : ESP32-C3 avec Tasmota
- **Protocole** : MQTT
- **Broker** : Mosquitto (installé sur le même NUC que OpenHab)
- **Serveur domotique** : OpenHab (en conteneur Docker)

---

### 1️⃣ Préparation côté Tasmota

Avant de configurer OpenHab, assurez-vous que votre ESP32-C3 :

- est connecté au Wi-Fi du MakerSpace
- publie les données MQTT correctement vers le broker (`172.16.4.33`)
- a un **Topic** unique (par exemple : `capteur`)

👉 Voir la section **6.1 Programmation des ESP32 avec Tasmota** pour plus de détails sur cette configuration.

---

### 2️⃣ Ajouter le binding MQTT dans OpenHab

1. Connectez-vous à l'interface Web d’OpenHab (`http://<IP_NUC>:8080`)
2. Allez dans **Paramètres > Add-ons > Bindings**
3. Recherchez **MQTT Binding**
4. Cliquez sur **Install**

---

### 3️⃣ Configurer le broker MQTT dans OpenHab

1. Allez dans **Paramètres > Things**
2. Cliquez sur **+ Ajouter un Thing**
3. Choisissez **MQTT Broker**
4. Remplissez les champs suivants :

| Champ           | Valeur                  |
|-----------------|--------------------------|
| Name            | Mosquitto Broker         |
| Broker Address  | `tcp://172.16.4.33:1883` |
| Client ID       | openhab                  |
| Secure          | désactivé (non TLS)      |
| Authentication  | désactivée (si pas d’utilisateur) |

---

### 4️⃣ Ajouter un capteur Tasmota (MQTT Generic Thing)

Chaque ESP32-C3 (ou "capteur") est représenté dans OpenHab par un **Thing MQTT Generic**.

#### Exemple : capteur avec topic `capteur`

1. Allez dans **Paramètres > Things > + Ajouter un Thing**
2. Choisissez **Generic MQTT Thing**
3. Choisissez comme bridge le **Mosquitto Broker**
4. Remplissez :

| Champ            | Valeur     |
|------------------|------------|
| Thing ID         | capteur    |
| Label            | Capteur ESP32C3 |
| MQTT Base Topic  | `tele/capteur/SENSOR` |

> Ce chemin est celui utilisé par Tasmota pour publier les données de capteurs (topic `tele/.../SENSOR`).

---

### 5️⃣ Ajouter les channels (données du capteur)

Ajoutez ensuite les **Channels** correspondant aux données publiées dans le message JSON de Tasmota.

#### 💧 Température (AMS2302)

```json
{
  "Time": "2025-06-13T12:07:23",
  "AM2301": {
    "Temperature": 24.7,
    "Humidity": 49.5
  }
}
```

🔹 Pour récupérer la température :

- Type : Number
- Label : Température
- MQTT State Topic : `tele/capteur/SENSOR`
- Transformation : `JSONPATH:$.AM2301.Temperature`

🔹 Pour l’humidité :

- JSONPATH : `$.AM2301.Humidity`

---

#### 🌫️ Particules fines (PMS7003 détecté comme PMS5003)

```json
"PMS5003": {
  "PM1.0": 6,
  "PM2.5": 10,
  "PM10": 14
}
```

🔹 PM2.5 par exemple :

- Type : Number
- Label : Poussières PM2.5
- MQTT State Topic : `tele/capteur/SENSOR`
- Transformation : `JSONPATH:$.PMS5003["PM2.5"]`

> Les autres données (PM1.0, PM10) peuvent être ajoutées de la même manière.

---

### 6️⃣ Lier les channels à des Items

1. Une fois les channels ajoutés, cliquez sur **Créer un nouvel Item** pour chacun.
2. Choisissez un nom et une icône (ex. `temperature_cuisine`, icône : `temperature`).
3. Cochez "Visible dans le model" si vous voulez l’utiliser dans l’UI.

---

### 7️⃣ Visualisation dans l’interface utilisateur

- Allez dans **Pages > Ajouter un bloc**
- Sélectionnez **Élément de type Gauge**, **Stat**, ou **Line Chart**
- Choisissez l’Item correspondant (température, humidité, particules, etc.)

> Vous pouvez créer des dashboards personnalisés pour différentes zones du MakerSpace.

---

### 📚 Documentation officielle OpenHab

La documentation d’OpenHab est très complète et bien structurée. En cas de doute sur un binding, une syntaxe ou une règle :

🔗 [https://www.openhab.org/docs/](https://www.openhab.org/docs/)

Elle propose :

- des tutos pour débuter
- des guides pour les bindings comme MQTT
- des exemples complets de transformations JSON, règles, pages UI, etc.

---

✅ À ce stade, les données envoyées par Tasmota sont reçues, transformées, et affichées dans OpenHab, prêtes à être utilisées dans des scénarios d’automatisation (cf. section 6.3).


---

### 6️⃣ Exemple de dashboard créé par Tamsota

<p align="center">
  <img src="images/photo1.png" alt="Photo 1" width="300" style="margin-right:10px;" />
  <img src="images/photo2.png" alt="Photo 2" width="300" />
</p>

