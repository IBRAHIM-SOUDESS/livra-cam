# 📦 LIVRA-CAM — Système de Gestion & Suivi Logistique avec QR Code Dynamique

> **Conçu et développé par [Moumbagna Nchare Ibrahim Soudess](https://github.com/Ibrah656im)**  
> *Étudiant en Informatique à l'Université de Yaoundé 1 | Passionné par la Cybersécurité et l'Intelligence Artificielle*

---

## 📌 Présentation du Projet

**Livra-Cam** est une solution complète de gestion des colis et de traçabilité logistique conçue pour les services de livraison et transporteurs au Cameroun. Elle automatise l'ensemble du cycle de vie des expéditions :

- **Portail Public de Suivi en Temps Réel** : Les clients consultent l'état de leur colis simplement grâce à leur numéro de suivi unique ou en scannant le QR code avec leur smartphone.
- **Moteur de Génération de QR Code Hybride** : Génération locale autonome (via `phpqrcode`) avec bascule automatique (*fallback*) vers une API cloud (`goqr.me`) pour une disponibilité 100%.
- **Impression d'Étiquettes Colis Normalisées** : Module d'impression haute définition (`print_label.php`) avec QR code prêt à coller sur les colis.
- **Tableau de Bord Administrateur & Gestionnaire** : Enregistrement des réceptions, changement d'étapes (En attente, Expédié, En transit, Livré), recherche et filtrage.
- **Rapports Quotidiens Automatisés** : Statistiques journalières sur le volume des colis et le chiffre d'affaires des expéditions.

---

## 🔒 Principes de Sécurité & Robustesse

Développé selon les exigences de sécurité des systèmes d'information :

1. **Défense Active contre les Injections SQL** :
   ```php
   // Configuration PDO stricte dans config.php
   $pdo->setAttribute(PDO::ATTR_EMULATE_PREPARES, false);
   $pdo->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
   ```
   Toutes les requêtes utilisent des instructions préparées natives côté serveur MySQL sans émulation logicielle.
2. **Authentification d'Administration Sécurisée** : Protection de l'espace d'administration via sessions PHP contrôlées et redirection systématique en cas d'accès non autorisé.
3. **Protection contre la Fuite d'Informations Techniques** : Messages d'erreur génériques en environnement de production afin de masquer les détails d'implémentation de la base de données.

---

## 🗄️ Schéma de la Base de Données

Le schéma `database.sql` comprend notamment :
- `colis` : `id`, `tracking_number`, `destinataire_nom`, `destinataire_telephone`, `ville_depart`, `ville_arrivee`, `poids`, `prix`, `statut`, `date_creation`, `historique_statuts`.
- `admins` : Identifiants et hachages des comptes administrateurs.

---

## 🚀 Installation & Déploiement Local

### Prérequis
- Serveur Web (**WampServer**, **XAMPP**, etc.)
- **PHP** 7.4+ ou 8.x avec extensions `pdo_mysql` et `gd` (pour les images QR code)
- **MySQL** / MariaDB

### Étapes
1. Déposer le dossier dans votre serveur local (ex. `C:/wamp64/www/livra-cam`).
2. Créer la base de données MySQL :
   ```sql
   CREATE DATABASE livra_cam_db CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
   ```
3. Exécuter le script SQL `database.sql`.
4. Vérifier les identifiants de connexion dans `config.php`.
5. Ouvrir l'application dans votre navigateur :  
   - Espace public : `http://localhost/livra-cam/`  
   - Administration : `http://localhost/livra-cam/admin.php`

---

## 👨‍💻 Auteur & Contact

- **Auteur** : Moumbagna Nchare Ibrahim Soudess
- **Portfolio** : [portfolio-ibrahim-kohl.vercel.app](https://portfolio-ibrahim-kohl.vercel.app/)
- **LinkedIn** : [moumbagna-nchare-ibrahim-soudess-85072a390](https://www.linkedin.com/in/moumbagna-nchare-ibrahim-soudess-85072a390)
- **Email** : `ibrahimsoudess7@gmail.com`
- **WhatsApp** : `+237 689 98 18 51`
