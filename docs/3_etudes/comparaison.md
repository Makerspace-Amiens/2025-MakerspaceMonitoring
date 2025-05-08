---
layout: default
title: 📊 Critères de comparaison
parent: 3. Étude des solutions domotiques open-source
nav_order: 14
---

# 📊 Critères de comparaison

Pour évaluer les différentes solutions domotiques open-source, plusieurs critères ont été définis. Ces critères permettent de comparer les plateformes de manière objective et de déterminer celle qui convient le mieux aux besoins du MakerSpace.

## Home Assistant

**Créé en 2013 par Paulus Schoutsen, un développeur néerlandais**, Home Assistant est rapidement devenu l'une des plateformes domotiques open-source les plus populaires.

### ✅ Avantages :
- Interface moderne et agréable.
- Très grande communauté active.
- Intégration facile avec de nombreux appareils (Zigbee, MQTT, ESPHome, etc.).
- Documentation abondante et maintenue.

### ❌ Inconvénients :
- Installation parfois capricieuse (notamment sur systèmes non dédiés).
- Certaines fonctionnalités avancées nécessitent une courbe d’apprentissage importante.
- Dépendance à YAML pour les configurations complexes.

## OpenHab

**Lancé en 2010 par Kai Kreuzer, un développeur allemand**, OpenHab est l'une des plateformes domotiques open-source historiques. Son architecture modulaire en fait un choix solide pour des déploiements évolutifs et personnalisés.

### ✅ Avantages :
- Architecture **modulaire** robuste adaptée à des scénarios complexes.
- Large **compatibilité** avec les protocoles domotiques existants.
- Interface personnalisable via plusieurs interfaces web (Main UI, Basic UI, HABPanel).
- Documentation riche et précise.
- Excellent support communautaire, en particulier pour les utilisateurs avancés.
- Fonctionne bien sur systèmes embarqués comme Raspberry Pi, mais aussi sur des serveurs plus robustes.
- Prise en charge native de **règles automatisées avancées** (DSL ou Blockly, scripts en JS).

### ❌ Inconvénients :
- Moins « prêt à l'emploi » : requiert un temps d’apprentissage.
- Interfaces graphiques moins modernes par défaut (mais personnalisables).

## Nymea

**Développé à partir de 2016 par une équipe dirigée par Simon Stürz**, Nymea se distingue par sa simplicité et sa légèreté.

### ✅ Avantages :
- Interface simple et efficace.
- Très facile à prendre en main, même pour des débutants.
- Léger, idéal pour des déploiements embarqués à ressources limitées.
- API claire et bien documentée.

### ❌ Inconvénients :
- Moins d’intégrations disponibles que Home Assistant ou OpenHab.
- Moins connu, donc communauté plus restreinte.
- Moins de possibilités de personnalisation avancée.

## Gladys Assistant

**Créé en 2014 par Pierre-Gilles Leymarie**, Gladys est un assistant domotique français centré sur la simplicité et l’efficacité locale.

### ✅ Avantages :
- Hébergement local par défaut, respectueux de la vie privée.
- Interface conviviale et simple à utiliser.
- Documentation en français, accessible.
- Développement actif avec orientation "plug and play".

### ❌ Inconvénients :
- Moins de plugins et d’intégrations comparé à Home Assistant ou OpenHab.
- Fonctionnalités avancées parfois limitées pour des projets complexes.
- Moins adapté à une architecture domotique multi-utilisateur ou multi-site.

---
