# 🛠️ Guide d’installation — MCZ Eco 2.0 Smart Control

---

## 📦 Présentation

Ce guide explique comment installer et configurer le système domotique permettant de piloter un poêle à pellets **MCZ Eco 2.0** via Home Assistant.

Le contrôle s’effectue à travers :

- Une télécommande RF modifiée  
- Des relais / optocoupleurs pilotés par ESP  
- Des automatisations Home Assistant  
- Des capteurs de température et de niveau pellets  

---

## 1️⃣ Prérequis

### 🖥️ Domotique

- Home Assistant opérationnel  
- ESPHome installé  
- Accès SSH / File Editor  
- HACS (optionnel mais recommandé)  

### 📡 Réseau

- Wi-Fi stable  
- IP fixe conseillée pour les ESP  

### 🔥 Poêle

- MCZ Eco 2.0  
- Télécommande RF fonctionnelle  

---

## 2️⃣ Matériel nécessaire

### 🔌 Électronique

- ESP32 / ESP8266  
- Optocoupleurs  
- Réducteurs de tension  
- Résistances  
- Alimentation USB  

### 📏 Capteurs

- VL53L0X (niveau pellets)  
- Capteur température salon  

### 🧰 Divers

- Câbles Dupont  
- Fer à souder  
- Boîtier imprimé 3D (optionnel)  

---

## 3️⃣ Flash des ESP (ESPHome)

### Étapes

1. Installer ESPHome dans Home Assistant  
2. Créer un nouvel appareil  
3. Coller le firmware présent dans :

esphome/

### Exemples

- `telecommande_poele.yaml`  
- `capteur_pellets.yaml`  

4. Compiler  
5. Flasher en USB  
6. Connecter au Wi-Fi  

---

## 4️⃣ Intégration dans Home Assistant

Une fois flashé :

- Les entités apparaissent automatiquement  

Vérifier la présence de :

switch.telecommande_poele_*
sensor.niveau_pellet_*

---

## 5️⃣ Installation des Helpers

Importer le fichier :

helpers/helpers_poele.yaml


Ou créer manuellement :

### Input Number

- Température cible poêle  
- Température secours  
- Flamme actuelle  
- Ventilation actuelle  

### Input Boolean

- Boost actif  
- Verrou réglage poêle  

### Input Datetime

- Heures démarrage / arrêt  
- Horodatage verrou  
- Dernier remplissage  

---

## 6️⃣ Installation des Sensors

Copier les fichiers :

sensors/


Contenu :

- Calcul autonomie  
- Consommation pellets  
- Temps de chauffe  
- Heures démarrage calculées  
- Température sécurisée  

Redémarrer Home Assistant.

---

## 7️⃣ Installation des Scripts

Importer :

scripts/


Contenu :

- ON / OFF sécurisé  
- Boost démarrage  
- Calibration  
- Réglages flamme 1 → 5  
- Réglages ventilation 1 → 5  

Chaque script reproduit une action télécommande.

---

## 8️⃣ Installation des Automatisations

Importer :

automations/


### 🔥 Démarrage

- Matin adaptatif  
- Soir adaptatif  

### ⏹️ Arrêt

- Arrêt matin  
- Arrêt soir  

### 🧠 Régulation

- Gestion flamme + ventilation fusionnée  

### 🪵 Pellets

- Détection remplissage  
- Alertes niveau bas  

---

## 9️⃣ Tableau de bord

Importer la vue Lovelace :

dashboard/poele.yaml


### Fonctions disponibles

- État poêle  
- Température  
- Niveau pellets  
- Autonomie  
- Consommation  
- Commandes manuelles  
- Planning  

---

## 🔟 Vérifications finales

Avant mise en production :

- ✔ Test ON / OFF  
- ✔ Test flamme 1 → 5  
- ✔ Test ventilation  
- ✔ Vérif température  
- ✔ Vérif capteur pellets  
- ✔ Vérif autonomie  

---

## 1️⃣1️⃣ Calibration initiale

Au premier démarrage :

1. Allumer le poêle  
2. Attendre 10 min  
3. Lancer calibration :

script.calibration_complete_poele


Permet de synchroniser :

- Télécommande  
- Home Assistant  
- Automatisations  

---

## 1️⃣2️⃣ Sauvegarde recommandée

Sauvegarder :

- Home Assistant  
- ESPHome  
- GitHub repo  

---

## ✅ Installation terminée

Le système est maintenant capable de :

- Démarrer automatiquement  
- Réguler la puissance  
- Adapter la ventilation  
- Calculer l’autonomie  
- Détecter les remplissages  

---




