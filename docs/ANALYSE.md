---
layout: home
title: 2. 📝 Analyse des besoins et cahier des charges
nav_order: 3
---

# 🔧 Contraintes imposées

Notre projet est sujet à plusieurs contraintes techniques et organisationnelles qui nécessitent une attention particulière.

1. **Utilisation de solutions open-source** : La conception du système repose sur l'utilisation de plateformes domotiques open-source.

2. **Connectivité** : Les capteurs et dispositifs doivent être compatibles avec des protocoles standardisés comme le Wi-Fi et MQTT pour garantir une transmission sécurisée et fiable des données.

3. **Affichage** : Des écrans d'affichage doivent être intégrés dans le système pour une présentation claire et accessible des données collectées, permettant une visualisation en temps réel pour les utilisateurs.

4. **Compatibilité des capteurs** : Les capteurs choisis doivent être compatibles avec les microcontrôleurs ESP32 et être en mesure de mesurer divers paramètres environnementaux tels que la température, l'humidité, la qualité de l'air et la consommation d'énergie.

5. **Interface utilisateur** : L'interface doit être conviviale et intuitive, permettant aux utilisateurs de configurer facilement des automatisations et de recevoir des alertes en cas de situations anormales.

6. **Sécurité et fiabilité** : Le système doit être conçu pour garantir la sécurité des données et la fiabilité des communications en utilisant des protocoles de chiffrement et des mécanismes de redondance si nécessaire.

---

# 👥 Usagers ciblés et leurs attentes

Le système de monitoring domotique du MakerSpace a été conçu pour répondre aux besoins de divers utilisateurs, tels que :

1. **👨‍🎓 Étudiants** :
   - Fonctionnalités permettant un accès aisé aux données environnementales.
   - Alertes en cas de conditions anormales détectées.
   - Interface intuitive facilitant la mise en place d'automatisations.

2. **👩‍🏫 Encadrants** :
   - Surveillance fiable assurant la sécurité des utilisateurs.
   - Outils d'analyse des données disponibles pour une meilleure compréhension.
   - Génération de rapports permettant d'évaluer l'utilisation de l'espace dans son ensemble.

3. **👨‍💼 Visiteurs** :
   - Écrans d'affichage clairs et bien visibles.
   - Instructions simples pour une utilisation optimale du système.
   - Interface conviviale offrant un accès facile aux informations nécessaires.

---

# 📝 Scénarios d’usage envisagés

Nous avons planifié de surveiller les trois principales zones du MakerSpace : le PrinterLAB, qui est équipé d'imprimantes 3D, le MecaLAB, comprenant une découpeuse laser et un atelier de bricolage, et enfin la salle robotique dédiée aux activités de robotique.

1. **🖨️ PrinterLAB** :
   - Surveillance de l'humidité
   - Contrôle de la température
   - Mesure de la qualité de l’air

2. **🔧 MecaLAB** :
   - Surveillance de l'humidité
   - Contrôle de la température
   - Mesure de la qualité de l’air
   - Mise en place d'un système d'automatisation : extinction automatique des équipements tels que la découpeuse laser pour des raisons de sécurité.

3. **🤖 Salle robotique** :
   - Surveillance de l'humidité
   - Contrôle de la température
   - Mesure de la qualité de l’air

---
