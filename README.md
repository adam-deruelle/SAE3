# ⚡ SAÉ 3 – Détection de charge d’un véhicule électrique (EV)

## 🎯 Objectif du projet

Concevoir un circuit électronique capable de détecter les différents états de charge d’un véhicule électrique via un capteur de courant et un traitement analogique. Le système doit activer un relais pour autoriser ou interdire la charge selon les signaux détectés.

## 🧩 Fonctionnement global

Le système s'appuie sur le standard **EVSE (Electric Vehicle Supply Equipment)** pour interpréter la tension envoyée par le véhicule électrique (VE) selon trois états :

| État | Description                              | Signal |
|------|------------------------------------------|--------|
| A    | Véhicule non connecté                    | +12V / -12V |
| B    | Véhicule connecté mais pas en charge     | +9V / -12V |
| C    | Véhicule connecté et en cours de charge  | Courant détecté |

## 🔌 Chaîne de traitement (schéma Proteus)

Le circuit intègre les éléments suivants :

- **ACS712ELCTR-05B** : capteur de courant fournissant une tension proportionnelle au courant détecté.
- **LF353** : amplificateur opérationnel utilisé pour le traitement du signal analogique.
- **LM393** : comparateurs pour discriminer les seuils et piloter un relais.
- **Relais QUAZ-SH-124** : commande physique de la charge.
- **Diodes de protection (D1, D2, D3)** : évitent les retours de tension.

📈 *Une courbe de sortie `Vout` est utilisée pour visualiser le comportement du capteur en fonction du courant réel.*

## 📊 États logiques de fonctionnement

```text
+------------------------+
| État A                |
| Véhicule non connecté |
| +12V / -12V           |
+------------------------+
         ↓
+----------------------------+
| État B                    |
| Véhicule connecté         |
| Pas de charge détectée    |
| +9V / -12V                |
+----------------------------+
         ↓
+----------------------------+
| État C                    |
| Véhicule en charge        |
| Courant mesuré détecté    |
+----------------------------+
```
