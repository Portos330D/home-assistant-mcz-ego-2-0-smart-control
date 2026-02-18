# 🔌 Schémas de câblage & principe de fonctionnement
## Interface Télécommande MCZ → ESP32

Suite aux retours de la communauté, cette section détaille le câblage complet entre la télécommande et l’ESP32, ainsi que le rôle des optocoupleurs.

---

# 🧠 Principe général

Le système ne pilote **pas directement le poêle**.

Il simule physiquement l’appui sur les boutons de la télécommande.

👉 L’ESP32 appuie “virtuellement” sur les boutons.

---

# 🔘 Repiquage des boutons

Chaque bouton tactile possède 2 pads.

Quand on appuie :

→ Les deux pads sont court-circuités.

Le repiquage consiste à souder 2 fils :

- 1 fil sur chaque pad  
- Sans injecter de tension  

---

## 📸 Exemple ON / OFF

*(Schéma + photo à insérer)*

Les deux points entourés correspondent au contact du bouton.

---

# 🔌 Où vont les fils ?

Chaque paire de fils part vers :

👉 Un optocoupleur

Pad 1 ───────┐
            ├── Optocoupleur ─── ESP32 GPIO
Pad 2 ───────┘

---

# 🔦 Rôle de l’optocoupleur

Un optocoupleur est un relais optique.

Il permet :

- D’isoler électriquement la télécommande  
- D’éviter toute injection de courant  
- De simuler un appui bouton  

---

## ⚙️ Fonctionnement interne

Quand le GPIO s’active :

1. LED interne s’allume  
2. Phototransistor se ferme  
3. Circuit bouton se ferme  
4. Télécommande détecte un appui  

👉 Exactement comme un doigt.

---

# 🧷 Important

On ne relie **jamais** :

- GND ESP ↔ télécommande  
- VCC ESP ↔ télécommande  

Isolation totale obligatoire.

---

# 🔌 Schéma de câblage complet

## Boutons → Optocoupleurs

| Bouton | GPIO ESP32 |
|--------|-------------|
| ON/OFF | GPIO14 |
| SET | GPIO27 |
| MODE | GPIO26 |
| ENTER | GPIO25 |
| UP | GPIO33 |
| DOWN | GPIO32 |

*(Adaptable selon configuration)*

---

## Alimentation

| Module | Alimentation |
|--------|---------------|
| ESP32 | 5V USB |
| Optocoupleurs | 5V ESP |
| Télécommande | Alimentation régulée |

---

# 📟 Correspondance avec ESPHome

Extrait YAML :

```yaml
switch:
  - platform: gpio
    pin: 14
    name: "Poele ON OFF"
