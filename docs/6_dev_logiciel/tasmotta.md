---
layout: default
title: programmation des esp32
parent: developpement logiciel
nav_order: 1
---

# 6.1 Programmation des ESP32

Dans le cadre du développement de notre système domotique pour le MakerSpace, la programmation des microcontrôleurs constitue une étape essentielle 🧠. L’objectif est simple : capter les données, les transmettre de façon fiable, et permettre au système de réagir intelligemment. Pour ça, on a misé sur un duo gagnant : un **matériel miniaturisé mais puissant**, et un **firmware déjà bien rodé**. Résultat : moins de galères de code, plus de stabilité et une mise en service accélérée 🚀.

## 🧱 Le choix du microcontrôleur : Seeed Studio XIAO ESP32-C3

Notre projet repose sur l’utilisation des cartes **XIAO ESP32-C3** de Seeed Studio. Ces microcontrôleurs ultra-compacts intègrent une puce **ESP32**, connue pour ses capacités Wi-Fi et Bluetooth, tout en tenant dans un format minuscule (21 x 17,5 mm). Autrement dit : **tout ce qu’il nous fallait pour rester discrets dans les labs** (et les boîtiers imprimés en 3D).

Parmi les avantages du XIAO :
- ✅ Format réduit, parfait pour l’intégration dans des espaces restreints
- ✅ Connectivité sans fil native : Wi-Fi + BLE
- ✅ Port USB-C, pas de convertisseur à rajouter
- ✅ Compatible avec Arduino, PlatformIO, Tasmota, etc.

> 🧪 Ces cartes sont connectées à des capteurs environnementaux (température, CO₂, humidité, consommation électrique...) et installées dans le PrintLab, le MécaLab et le MediaLab.

![XIAO ESP32](https://files.seeedstudio.com/wiki/XIAO-ESP32/images/xiao-esp32-banner.jpg)

---

## ⚙️ La solution rapide et stable : Tasmota

Au départ, on pensait tout programmer “à la main” en **Arduino C++** ou en **MicroPython**. Mais après quelques tests (et des heures de debug 🫠), on a rapidement vu que ça allait être long. Très long. Et comme l’objectif du projet est aussi d’avoir **un déploiement efficace**, on a pris une décision stratégique : utiliser **Tasmota**.

### 🧠 C’est quoi Tasmota ?

Tasmota, c’est un firmware open-source développé à l’origine pour les modules ESP8266, et aujourd’hui compatible avec les ESP32. Il permet de transformer un microcontrôleur en **dispositif domotique configurable par interface web**. Pas besoin d’écrire une ligne de code 🧙.

### 🎁 Ce que ça nous apporte :
- 🖥️ Interface web intégrée pour tout configurer
- 📡 Support MQTT natif → intégration directe dans Home Assistant
- 🔌 Reconnaissance facile des capteurs (DHT, MH-Z19, capteur de conso...)
- ♻️ Mises à jour OTA possibles
- 🏁 Mise en service en quelques minutes par module

![Interface Tasmota](https://tasmota.github.io/docs/_media/WebUI-MQTT-Configuration.png)

---

## 🔧 Mise en place concrète

Chaque XIAO ESP32 est flashé avec la version Tasmota pour **ESP32-C3**. Lors du premier démarrage :
1. Un réseau Wi-Fi local est généré.
2. On se connecte via smartphone ou PC.
3. On accède à l’interface pour :
   - Nommer l’appareil (ex: `printlab_air1`)
   - Définir les GPIO utilisés (entrée, capteur, etc.)
   - Configurer le serveur MQTT (adresse, topic, identifiants)
   - Vérifier les logs en live.

> 🧩 Une fois configuré, l’appareil publie automatiquement ses données vers Home Assistant, sans recoder ni recompiler.

---

## 🌐 Une intégration fluide dans l’écosystème

Le système Home Assistant récupère les données via MQTT et les transforme en entités exploitables : température, taux de CO₂, consommation, etc. Ces entités peuvent ensuite déclencher des **scénarios** définis dans la section suivante (ex: activer la ventilation si la température dépasse 27°C dans le MécaLab).

Ce choix technique nous a permis de :
- Déployer plus rapidement les modules ⚡
- Réduire les bugs liés au code 🐛
- Centraliser facilement les configurations 🧩
- Gagner du temps pour les autres parties du projet (dashboard, scénarios, tests…)

---

## 🔗 Pour aller plus loin

- [📘 Documentation officielle Tasmota](https://tasmota.github.io/docs/)
- [🔬 XIAO ESP32 chez Seeed Studio](https://www.seeedstudio.com/XIAO-ESP32-C3-p-5431.html)
- [🔧 Tasmota for ESP32 GitHub](https://github.com/arendst/Tasmota)

---

🛠️ *Conclusion* : Grâce à ce combo **XIAO ESP32 + Tasmota**, on a trouvé une approche stable, rapide et efficace pour connecter tous les espaces du MakerSpace. Et surtout, on a pu se concentrer sur l’essentiel : ce que le système doit faire, pas comment le coder ligne par ligne 😄
