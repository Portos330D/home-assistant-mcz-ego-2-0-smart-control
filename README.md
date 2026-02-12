🔥 MCZ Ego 2.0 — Smart Control via Home Assistant

Projet complet de gestion domotique intelligente d’un poêle à pellets MCZ Eco 2.0 piloté via télécommande RF non connectée.

---

⚠️ Particularité du projet

Le poêle n’est pas connecté nativement.

Contrôle réalisé via :

- Télécommande RF d’origine
- Reproduction des commandes
- Pilotage IR / RF via Home Assistant
- Scripts d’émulation boutons

👉 Aucun accès direct au firmware MCZ.

---

🎯 Objectifs

- Chauffage adaptatif intelligent
- Anticipation thermique matin / soir
- Gestion automatique flamme + ventilation
- Sécurité niveau pellets
- Détection remplissage trémie
- Calcul autonomie temps réel
- Dashboard supervision complet

---

🧠 Logique de fonctionnement

Le système ajuste automatiquement :

- Niveau de flamme (1 → 5)
- Ventilation (1 → 5)
- Heures de démarrage
- Temps d’anticipation
- Boost thermique

Selon :

- Température salon
- Température cible
- Vitesse de chauffe estimée
- Niveau pellets
- Heure / nuit
- Semaine vs week-end

---

🛠️ Architecture technique

Équipement| Rôle
Home Assistant| Cerveau logique
ESPHome| Capteur pellets
Capteur température| Référence thermique
Télécommande RF| Interface poêle
Scripts HA| Émulation boutons

---

📡 Pilotage du poêle

Commandes reproduites :

- ON / OFF
- Flamme 1 → 5
- Ventilation 1 → 5
- Mode Auto

Via scripts :

script.flamme_niveau_1 → 5
script.ventilation_1 → 5
script.poele_on_off

---

🪵 Gestion pellets

Capteur :

- VL53L0X (distance laser)
- Correction entonnoir
- Calcul %

Fonctions :

- Autonomie restante
- Consommation kg/h
- Détection remplissage
- Compteur sacs

---

🛡️ Sécurités intégrées

- Blocage démarrage < 10 %
- Anti double démarrage
- Verrou commandes RF
- Fallback température HS
- Anti-spam réglages

---

📊 Dashboard inclus

- Consigne température
- Temps chauffe estimé
- Démarrage calculé matin / soir
- Niveau pellets %
- Consommation temps réel
- Autonomie restante

---

🚀 Installation

1. Copier dossiers dans "/config/"
2. Importer helpers
3. Vérifier scripts RF
4. Redémarrer Home Assistant

---

⚠️ Disclaimer

Projet non officiel MCZ.

Aucune modification interne du poêle.
Pilotage externe uniquement via télécommande.

---

📌 Auteur

Projet domotique personnel avancé — optimisation thermique pellets.
