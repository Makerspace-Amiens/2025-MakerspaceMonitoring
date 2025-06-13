---
layout: default
title: 6. Développement logiciel
nav_order: 27
has_children: true
---
# 🧠 6. Développement logiciel

Cette partie explique comment on a codé, configuré et testé le système qui fait tourner toute l'automatisation du MakerSpace.

> 🛠️ Objectif : connecter les capteurs, centraliser les données, déclencher les bonnes actions au bon moment.  
> L'ensemble repose sur des **ESP32C3**, **MQTT**, et **OPENHAB**.

---

## 🗂️ Sommaire interactif

### 🔌 [6.1 Programmation des ESP32](programmation_esp32.md)
📎 Langages utilisés : `MicroPython`, `Arduino C++`  
🧰 IDE : `PlatformIO`, `Thonny`, `Arduino IDE`  
🧠 Ce qu’on a codé pour capter, envoyer et réagir à des données.

---

### ⚙️ [6.2 Configuration de la solution domotique](6_2_configuration_domotique.md)
🧠 On a choisi **OPENHAB** pour centraliser les capteurs.  
📡 Intégration avec `MQTT`, création des entités, dashboard de suivi.

---

### 🤖 [6.3 Automatisations et scénarios](6_3_automatisations_scenarios.md)
🚨 Alerte CO₂, 🔁 ventilation auto, 📊 suivi conso électrique  
On explique nos règles domotiques (en YAML) et comment elles réagissent en temps réel.

---




🧑‍💻 **Code source dispo ici :** [🔗 GitHub du projet](https://github.com/tonrepo)

---



