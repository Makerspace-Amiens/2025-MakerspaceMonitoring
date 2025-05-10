---
layout: default
title: developpement logiciel
nav_order: 1
has_children: true
---

# 6. Développement logiciel

Cette section décrit tout ce qu’on a mis en place côté logiciel pour faire tourner le système domotique du MakerSpace.  
On y parle surtout de la programmation des microcontrôleurs (ESP32), de la config de Home Assistant, des automatisations et des tests.

Le but : avoir un système fiable, simple à maintenir et bien intégré dans le PrintLab, MécaLab et MediaLab.

## Ce qu’on trouve dans cette partie :

- [6.1 Programmation des ESP32](6_1_programmation_esp32.md)  
  Les outils et langages qu’on a utilisés (MicroPython, Arduino C++), les bibliothèques, et comment on a structuré le code.

- [6.2 Configuration de la solution domotique](6_2_configuration_domotique.md)  
  Comment on a paramétré Home Assistant pour récupérer les données des capteurs via MQTT, les afficher et déclencher des actions.

- [6.3 Automatisations et scénarios](6_3_automatisations_scenarios.md)  
  Quelques exemples concrets d'automatisations : alertes CO₂, gestion de la température, suivi des consommations.

- [6.4 Tests et validation](6_4_tests_validation.md)  
  Comment on a vérifié que tout fonctionne bien, capteur par capteur et scénario par scénario.

---

> Cette partie est à jour avec la dernière version du système. Si des modifs sont faites côté code, pensez à mettre à jour aussi cette section.

