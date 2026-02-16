# 🪵 MCZ EGO 2.0 — Smart Control via Home Assistant

Système complet de pilotage intelligent pour poêle à pellets **MCZ EGO 2.0** basé sur **Home Assistant**, utilisant l’émulation de télécommande RF pour automatiser la gestion thermique, la ventilation, la sécurité et la consommation.

---

## 🎯 Objectif du projet

Rendre un poêle **MCZ EGO 2.0 non connecté** entièrement domotisable grâce à Home Assistant :

- 🔁 Pilotage RF automatisé  
- 🌡️ Gestion thermique adaptative  
- ⏱️ Anticipation des démarrages  
- 🪵 Sécurité niveau pellets  
- 📦 Détection remplissage  
- 📊 Calcul d’autonomie  
- 🖥️ Dashboard temps réel  

---

## 🔧 Installation matérielle

**Configuration utilisée :**

| Équipement | Modèle / Méthode |
|------------|------------------|
| Poêle | MCZ EGO 2.0 |
| Télécommande | RF d’origine |
| Contrôle | Pont RF / IR émulé |
| Température salon | Capteur Tuya Wi-Fi |
| Niveau pellets | VL53L0X — ESPHome |

## 🧰 Matériel utilisé

### 🔌 Optocoupleur 

**Rôle :**  
Permet d’isoler électriquement les commandes envoyées par l’ESP / relais vers la télécommande RF du poêle MCZ.

**Utilisé pour :**
- ON / OFF poêle
- Navigation menu
- Simulation boutons télécommande

**🔗 Produit :**  
https://a.aliexpress.com/_EH5B23W

---

### 📏 Capteur de distance — VL53L0X

**Rôle :**  
Capteur laser Time-of-Flight utilisé pour mesurer la hauteur de pellets dans la trémie.

**Permet de calculer :**
- % de remplissage
- Kg restants
- Autonomie
- Détection remplissage sac

**🔗 Produit :**  
https://a.aliexpress.com/_EG5FWQk

---

### 🔋 Réducteur de tension (Step-Down)

**Rôle :**  
Convertisseur DC-DC permettant d’abaisser une tension (ex : 12V) vers :

- 5V  
- 3.3V  

**Utilisé pour alimenter :**
- ESP32 / ESP8266
- Capteurs
- Modules relais

**🔗 Produit :**  
https://a.aliexpress.com/_EJ90bfS

---

### 🖥️ Module / Carte électronique

**Rôle :**  
Module électronique utilisé dans le projet (interface / traitement / support matériel selon montage exact).

👉 À détailler selon la configuration matérielle utilisée.

**🔗 Produit :**  
https://a.aliexpress.com/_EJ3c2jA

---

### 🧮 Résistances

**Rôle :**  
Utilisées pour :

- Pull-up / Pull-down
- Protection GPIO
- Adaptation tension signaux
- Circuits optocoupleurs

**🔗 Produit :**  
https://a.aliexpress.com/_EwOxeic

### 🧠 Microcontrôleur — ESP32

**Rôle :**  
Microcontrôleur principal du projet, utilisé pour piloter les commandes, capteurs et automatisations.

Il assure :

- Communication avec Home Assistant (API / MQTT)
- Exécution des scripts ESPHome
- Pilotage optocoupleurs / relais
- Gestion capteurs (VL53L0X, température, etc.)
- Automatisations locales sécurisées

**Fonctions utilisées dans le projet :**

- Simulation boutons télécommande
- Gestion séquences d’allumage
- Calibration flamme / ventilation
- Supervision état système

**🔗 Produit :**  
https://a.aliexpress.com/_EHOsCpa

---

## 🧠 Fonctionnalités

### 🔥 Gestion thermique intelligente

- Démarrage adaptatif matin  
- Démarrage adaptatif soir  
- Différenciation semaine / week-end  
- Anticipation selon température réelle  
- Mode Boost automatique  

---

### 🌪️ Gestion flamme + ventilation fusionnée

- Pilotage synchronisé flamme / ventilation  
- Adaptation selon écart température cible  
- Limitation nocturne automatique  
- Séquences RF temporisées  
- Verrou anti-collision commandes  

---

### 🪵 Gestion pellets

- Blocage démarrage si niveau **< 10 %**  
- Calcul autonomie restante  
- Calcul consommation **kg/h**  
- Moyenne glissante 24 h  

---

### 📦 Détection remplissage

- Détection ajout sac pellets  
- Anti faux-positifs (bras / entonnoir)  
- Anti-spam temporel  
- Incrément compteur sacs consommés  

---

### 🛡️ Sécurités intégrées

- Fallback si capteur température indisponible  
- Verrou commandes RF  
- Anti-yoyo température (hystérésis)  
- Anti redémarrage multiple  
- Sécurité pellets bas  

---

## 🛠 Automatisations incluses

- Démarrage matin FULL adaptatif  
- Démarrage soir FULL adaptatif  
- Arrêt programmé matin  
- Arrêt programmé soir  
- Gestion flamme intelligente  
- Gestion ventilation intelligente  
- Fusion flamme + ventilation  
- Détection remplissage pellets  
- Sécurité niveau pellets  

---

## 📂 Structure du dépôt

automations/ → Logiques du poêle
scripts/ → Commandes RF / IR
helpers/ → Inputs / mémoires / verrous
sensors/ → Capteurs calculés
dashboard/ → Interface Lovelace
docs/ → Documentation technique


---

## 🚀 Installation

1. Copier les fichiers YAML dans Home Assistant  
2. Créer les helpers nécessaires  
3. Importer les automatisations  
4. Adapter les `entity_id`  
5. Lier les scripts RF à votre pont RF / IR  

---

## ⚠️ Avertissement

Projet **non affilié à MCZ**.

Utilisation à vos risques :

- Mauvaise configuration = risque de surchauffe  
- Toujours conserver les sécurités d’origine du poêle

---

## 🖥️ Interface Home Assistant

📊 Dashboard Lovelace

Ce projet inclut une vue complète Home Assistant pour la gestion du poêle MCZ Eco 2.0.

Fonctionnalités

- 🔥 Allumage / extinction sécurisé
- 🚀 Boost démarrage automatique
- 🌡️ Régulation intelligente température
- 🌪️ Gestion ventilation dynamique
- 🪵 Adaptation puissance selon niveau pellets
- ⏰ Programmation matin / soir

Installation

1. Copier le fichier :

lovelace/poele-dashboard.yaml

2. L’importer dans Home Assistant :

Paramètres → Tableaux de bord → Ajouter une vue YAML

3. Adapter les entités selon votre installation.

Aperçu

![Dashboard poêle](docs/images/Tableau_de_bord_ha.png)

---

## 🖨️ Intégration & boîtier 3D

### Montage final

![Support 3D 1](docs/images/support_3d_1.jpg)

![Support 3D 2](docs/images/support_3d_2.jpg)

![Support 3D 3](docs/images/support_3d_3.jpg)

Lien vers le boitier et support en impression 3D: (https://cults3d.com/fr/mod%C3%A8le-3d/maison/support-telecommande-boitier-pcb-mcz-ego-2-0-smart-control-home-assistant)

---

### 📏 Capteur de niveau pellets — VL53L0X (ToF)

**Rôle :**  
Capteur laser Time-of-Flight utilisé pour mesurer la hauteur de pellets dans la trémie du poêle.

Il permet une mesure sans contact, fiable même avec :

- Poussière
- Forme irrégulière des pellets
- Entonnoir de chute

---

### 🧠 Données calculées

Grâce aux calculs Home Assistant / ESPHome :

- % de remplissage
- Kg restants
- Autonomie restante
- Consommation kg/h
- Détection ajout sac
- Historique de niveau

---

### 🧱 Intégration mécanique

Le capteur est monté :

- En partie haute de la trémie
- Orienté verticalement vers les pellets
- Dans un support imprimé 3D
- Avec passage de câble latéral

Montage sans contact direct avec le combustible.

---

### 🖨️ Support 3D utilisé

Support compatible VL53L0X imprimé en 3D permettant :

- Fixation propre dans la trémie
- Protection du capteur
- Maintien de l’angle de mesure

**🔗 Modèle Thingiverse :**  
https://www.thingiverse.com/b487a4c7-b92a-4e0d-969d-48f4934fa842

---

### ⚙️ Caractéristiques capteur

- Technologie : Laser ToF
- Portée : ~2 m max
- Précision : ±3 mm
- Interface : I²C
- Alimentation : 3.3 V / 5 V

---

### 📸 Exemple d’intégration

Capteur installé dans la trémie avec support imprimé 3D, permettant une mesure continue du niveau de pellets sans modification du poêle.

---

### 🔗 Produit capteur

https://a.aliexpress.com/_EG5FWQk

---

## 📜 Licence

Licence **MIT** — libre d’utilisation et de modification.

---

## 🤝 Contribution

Projet personnel évolutif.

Les améliorations, retours d’expérience et idées sont les bienvenus.
