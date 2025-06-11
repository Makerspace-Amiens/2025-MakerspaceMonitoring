---
layout: home
title: 3. 🧰 Étude des solutions domotiques open-source
nav_order: 4
---

# 🏠 Présentation des solutions testées

Dans le cadre de ce projet, différentes solutions de domotique open-source ont été examinées afin de déterminer celle qui répond le mieux aux exigences du MakerSpace.

Le concept open source fait référence à une licence logicielle qui permet aux utilisateurs d'accéder, de modifier et de distribuer librement le code source du logiciel. Cela garantit la transparence, la flexibilité et l'extensibilité du système.

## <img src="images/HomeAssistant_Logo.png" alt="Logo Home Assistant" width="120"/>

### Home Assistant

Créée en 2013 par Paulus Schoutsen, Home Assistant s'est imposée comme l'une des plateformes de domotique open-source les plus populaires à l'échelle mondiale. Avec une communauté très active, Home Assistant propose une documentation complète, des mises à jour régulières et une interface utilisateur moderne et personnalisable.

**Documentation** : [Documentation Home Assistant](https://www.home-assistant.io/docs/)

---

## <img src="images/OPENHAB_Logo.png" alt="Logo OpenHAB" width="100"/>

### OpenHAB

Lancée en 2010 par Kai Kreuzer, OpenHAB (Open Home Automation Bus) se distingue par son architecture modulaire basée sur Java et OSGi, offrant ainsi une grande flexibilité dans l'ajout de fonctionnalités. Compatible avec une large gamme de protocoles, technologies et matériels, OpenHAB est une solution fiable et pérenne.

**Documentation** : [Documentation OpenHab](https://www.openhab.org/docs/)

---

## <img src="images/Nymea_Logo.png" alt="Logo Nymea" width="120"/>

### Nymea

Développée plus récemment par une équipe autrichienne, Nymea vise à simplifier la configuration et la gestion des systèmes domotiques. Avec une approche axée sur une expérience utilisateur fluide, Nymea propose une interface claire, un noyau léger et une compatibilité croissante avec une variété de capteurs, actionneurs et objets connectés.

**Documentation** : [Documentation Nymea](https://nymea.io/docs/)

---

## <img src="images/Gladys_Logo.png" alt="Logo Gladys Assistant" width="100"/>


### Gladys Assistant

Initié en 2013 par Pierre-Gilles Leymarie en tant qu'assistant personnel intelligent, Gladys Assistant est devenu une solution domotique complète. Reposant sur Node.js, le système se caractérise par sa facilité de déploiement et le respect de la confidentialité des données en local. Gladys propose une interface intuitive, un système de scénarios avancé et une intégration optimale avec les appareils IoT modernes.

**Documentation** : [Documentation Gladys Assistant](https://gladysassistant.com/docs/)

---

# 📊 Critères de comparaison

L'évaluation des différentes solutions domotiques open-source s'est basée sur des critères prédéfinis afin de comparer de manière objective les plateformes et de déterminer celle qui répond le mieux aux besoins du MakerSpace.

Home Assistant présente des avantages tels qu'une interface moderne et agréable, une grande communauté active, une intégration facile avec de nombreux appareils et une documentation abondante. Cependant, son installation peut parfois poser des problèmes, certaines fonctionnalités avancées nécessitent une courbe d'apprentissage importante et il dépend fortement de YAML pour les configurations complexes.

OpenHab se distingue par son architecture modulaire robuste adaptée à des scénarios complexes, sa large compatibilité avec les protocoles domotiques existants, ses interfaces web personnalisables et son excellent support communautaire. Néanmoins, il demande un temps d'apprentissage et ses interfaces graphiques de base sont moins modernes mais peuvent être personnalisées.

Nymea se distingue par son interface simple et efficace, sa facilité de prise en main même pour des débutants, sa légèreté idéale pour les déploiements embarqués et son API claire et bien documentée. Cependant, il offre moins d'intégrations que Home Assistant ou OpenHab, une communauté plus restreinte et moins de possibilités de personnalisation avancée.

Gladys Assistant offre un hébergement local par défaut respectueux de la vie privée, une interface conviviale et simple à utiliser, une documentation en français et un développement actif avec une orientation "plug and play". Cependant, il propose moins de plugins et d'intégrations que Home Assistant ou OpenHab, des fonctionnalités avancées parfois limitées pour des projets complexes et il est moins adapté à une architecture domotique multi-utilisateur ou multi-site.

---

# ⚖️ Tableau comparatif synthétique

| **Critère**   | <img src="images/HomeAssistant_Logo.png" alt="Logo Home Assistant" width="60"/><br>**Home Assistant** | <img src="images/OPENHAB_Logo.png" alt="Logo OpenHAB" width="60"/><br>**OpenHAB** | <img src="images/Nymea_Logo.png" alt="Logo Nymea" width="60"/><br>**Nymea** | <img src="images/Gladys_Logo.png" alt="Logo Gladys" width="60"/><br>**Gladys Assistant** |
|---------------|----------------------------------------------------------------|------------------------------------------------------------------|------------------------------------------------------------|---------------------------------------------------------------|
| **Ergonomie** | ⭐⭐⭐⭐☆<br>Interface claire, configuration assistée.             | ⭐⭐⭐☆☆<br>Interface moins intuitive, demande des bases techniques. | ⭐⭐⭐⭐☆<br>Interface simple, adaptée aux débutants.          | ⭐⭐⭐⭐☆<br>Interface intuitive, facile à utiliser.               |
| **Compatibilité** | ⭐⭐⭐⭐⭐<br>Supporte de nombreux protocoles et équipements.     | ⭐⭐⭐⭐⭐<br>Très large compatibilité, très complet.          | ⭐⭐⭐⭐☆<br>Bonne compatibilité, un peu plus limitée.         | ⭐⭐⭐⭐☆<br>Compatible avec la plupart des équipements courants. |
| **Documentation** | ⭐⭐⭐⭐☆<br>Documentation bien organisée avec des tutoriels.     | ⭐⭐⭐⭐⭐<br>Documentation très riche et détaillée.            | ⭐⭐⭐☆☆<br>Documentation courte, manque d’exemples.           | ⭐⭐⭐☆☆<br>Documentation parfois incomplète ou trop technique.   |
| **Communauté** | ⭐⭐⭐⭐⭐<br>Communauté active, entraide facile.                   | ⭐⭐⭐⭐⭐<br>Communauté présente et expérimentée.                    | ⭐⭐☆☆☆<br>Communauté plus réduite, en développement.        | ⭐⭐☆☆☆<br>Communauté plus restreinte, surtout francophone.     |
| **Extensibilité** | ⭐⭐⭐⭐☆<br>Nombreux modules, intégration flexible.             | ⭐⭐⭐⭐⭐<br>Architecture modulaire et très extensible.        | ⭐⭐⭐☆☆<br>Moins flexible, options limitées.                  | ⭐⭐⭐☆☆<br>Extensions possibles, mais moins nombreuses.           |
| **Sécurité**  | ⭐⭐⭐⭐☆<br>Bon niveau de sécurité, mises à jour régulières.       | ⭐⭐⭐⭐☆<br>Sécurité bien gérée, support SSL.                       | ⭐⭐⭐☆☆<br>Sécurité correcte pour un usage local.             | ⭐⭐⭐☆☆<br>Sécurité suffisante, mais dépend de la configuration.  |

---

# ✅ Choix de la solution retenue et justification

Initialement, notre préférence était pour Home Assistant, en raison de sa renommée, de son interface moderne et de sa communauté étendue. Cependant, un superviseur du MakerSpace a signalé plusieurs problèmes rencontrés lors de son utilisation (intégrations instables, configuration complexe).

Suite à ces retours, nous avons décidé de reconsidérer notre choix et de nous orienter vers **OpenHAB**, une solution plus fiable, mieux documentée, et avec une architecture modulaire adaptée à notre projet.

---
