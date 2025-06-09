---
layout: default
title: ✉️ Structure des messages échangés
parent: 5. Communication et interconnexion
nav_order: 24
---

# ✉️ Structure des messages échangés

Les capteurs envoient des messages au format JSON, un format léger, structuré et largement pris en charge. Cette méthode permet de transmettre diverses valeurs ou métadonnées dans un unique message, ce qui facilite les évolutions futures.

Exemple de message publié :
```json
{
  "valeur": 23.5,
  "unite": "°C",
  "timestamp": "2025-06-08T15:42:10Z"
}
```

---
