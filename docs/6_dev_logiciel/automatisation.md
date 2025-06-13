---
layout: default
title: Automatisation
parent: 6. Développement logiciel
nav_order: 29
---


## 🤖 6.3 Automatisations et scénarios

Les **automatisations** sont au cœur de toute solution domotique : elles permettent de faire réagir le système à des événements en temps réel. Dans un lieu aussi actif que le **MakerSpace**, elles rendent l’environnement **plus intelligent, sécurisé et autonome**.

Par exemple, une automatisation peut :

- déclencher un ventilateur si le taux de CO₂ est trop élevé,
- couper le courant d’un outil s’il chauffe,
- allumer l’éclairage automatiquement en fonction de la présence.

---

### 🎯 Objectif de cette démonstration

Pendant notre journée de présentation dans le **foyer**, nous avons mis en place une **démo de sécurité thermique** afin de montrer en pratique l’utilité du **monitoring intelligent**.

> L’idée : **chauffer un capteur** avec un **sèche-cheveux branché sur une prise connectée**, et dès que la température dépasse **30°C**, une **règle dans OpenHab** :
>
> 1. Allume un **ventilateur branché sur une autre prise connectée** (Tasmota)
> 2. Éteint le **sèche-cheveux automatiquement** pour éviter toute surchauffe

Ce scénario simple illustre bien comment la domotique peut être utilisée **pour surveiller et protéger l’environnement du MakerSpace**.

---

## ⚙️ Mise en place de l’automatisation dans OpenHab

Nous allons créer une **règle conditionnelle** dans OpenHab qui surveille un capteur de température, et agit automatiquement si une température critique est atteinte.

---

### 🧪 Matériel utilisé

| Équipement         | Détail                                          |
|--------------------|--------------------------------------------------|
| ESP32-C3 (Tasmota) | avec capteur **AM2302**                          |
| Prise connectée 1  | Branchée au **sèche-cheveux**                   |
| Prise connectée 2  | Branchée au **ventilateur** (commandée via Tasmota) |
| Plateforme         | OpenHab via Docker (NUC)                        |

---

### 📐 Étape 1 : Préparer les Items dans OpenHab

Assurez-vous que les éléments suivants sont bien configurés et visibles dans OpenHab :

| Item                | Type     | Exemple              |
|---------------------|----------|-----------------------|
| `temp_foyer`        | Number   | Température du capteur |
| `prise_ventilo`     | Switch   | ON/OFF via Tasmota     |
| `prise_sechecheveux`| Switch   | ON/OFF via Tasmota     |

> Ces Items doivent être reliés aux topics MQTT correspondants (voir section 6.2).

---

### ⚙️ Étape 2 : Créer une règle dans l'interface Web

1. Accédez à OpenHab via navigateur → **http://<IP_NUC>:8080**
2. Menu **Settings > Rules**
3. Cliquez sur **+ Add Rule**

#### 📋 Paramètres de la règle

- **Name** : Sécurité thermique foyer
- **Description** : Coupe le sèche-cheveux et active un ventilateur si température > 30°C
- **When (déclencheur)** :
  - Type : **Item**
  - Item : `temp_foyer`
  - Trigger : **changes**
  - Condition : **greater than 30**

#### ⚡ Action 1 : Allumer le ventilateur

- Type : **Run a rule action**
- Choisir : **Item Action**
- Item : `prise_ventilo`
- Commande : `ON`

#### 🔌 Action 2 : Éteindre le sèche-cheveux

- Ajouter une autre action
- Item : `prise_sechecheveux`
- Commande : `OFF`

---

### ✅ Résultat attendu

Lorsque la température dépasse **30°C**, le système :

1. Allume automatiquement le ventilateur
2. Coupe l’alimentation du sèche-cheveux
3. Les actions sont visibles dans le journal d’événements d’OpenHab

Ce type de scénario peut ensuite être enrichi (temporisation, notifications, seuils ajustables, etc.).

---

### 📚 Documentation OpenHab

La documentation officielle est claire et bien organisée, notamment pour :

- la création de règles :
  👉 https://www.openhab.org/docs/automation/
- la transformation de données (JSON, MAP, REGEX) :
  👉 https://www.openhab.org/docs/configuration/transformations.html
- les bindings et configurations MQTT :
  👉 https://www.openhab.org/addons/bindings/mqtt/

---

🧠 Grâce à ce système, nous avons démontré que la domotique ne se limite pas à du confort, mais peut aussi **jouer un rôle de sécurité proactive** dans un environnement collectif comme un MakerSpace.

