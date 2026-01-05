# Costume Rental App - Cahier des Charges

## 1. Présentation du Projet
L'application "Costume Rental" est une solution complète de gestion pour un service de location de costumes. Elle permet de gérer l'inventaire, la clientèle et le cycle de vie des locations.

## 2. Architecture Technique
- **Frontend** : Flutter (Multi-plateforme: Android, iOS, Windows)
- **Backend** : Flask (Python)
- **Base de données** : MySQL (Production) / SQLite (Développement/Alternative)
- **Communication** : API RESTful (JSON)

## 3. Spécifications Fonctionnelles - Back-End (Flask)
L'API Flask sert de moteur central pour la gestion des données et la logique métier.

### 3.1 Authentification
- Système d'accès sécurisé par **PIN Admin**.
- Décorateur `@admin_required` pour protéger les endpoints sensibles.

### 3.2 Gestion des Costumes (CRUD)
- Création, lecture, mise à jour et suppression des costumes.
- Attribution de catégories, tailles, descriptions et prix de location.
- Gestion du statut en temps réel : `disponible` ou `loué`.
- Module d'upload d'images avec génération de noms uniques (UUID).

### 3.3 Gestion des Clients
- Enregistrement des clients avec Nom, Téléphone, et CIN (Identifiant unique).
- Recherche de clients par CIN ou nom.

### 3.4 Gestion des Locations
- Création de contrats de location liant un client à un costume.
- Calcul automatique des dates de début et de fin.
- Mise à jour automatique de la disponibilité du costume lors de la location et du retour.
- Endpoint spécifique pour terminer une location et libérer le costume.

---

## 4. Spécifications Fonctionnelles - Front-End (Flutter)
L'interface est divisée en deux espaces ergonomiques et réactifs.

### 4.1 Interface Administrateur
- **Dashboard** : Vue d'ensemble des activités.
- **Gestion des Costumes** : Catalogue avec filtres (catégorie, taille, statut), ajout/édition avec support caméra/galerie pour les photos.
- **Gestion des Clients** : Listing complet, recherche rapide et formulaire d'ajout de client.
- **Suivi des Locations** : Historique des locations en cours et terminées, possibilité de marquer un retour.

### 4.2 Interface Client (Consultation)
- **Home Page** : Galerie visuelle des costumes disponibles.
- **Détails Costume** : Visualisation complète des informations avant location.

### 4.3 Expérience Utilisateur (UX)
- Navigation via `GoRouter`.
- Gestion d'état fluide avec `Provider`.
- Thème visuel moderne avec micro-animations.

---

## 5. Modèle de Données (Base de Données)
Le schéma de base de données comprend les entités suivantes :

### Table `costumes`
- `id` (PK), `nom`, `description`, `categorie`, `taille`, `prix_location`, `image_path`, `statut`.

### Table `clients`
- `id` (PK), `nom`, `prenom` (en local), `telephone`, `cin` (Unique).

### Table `locations`
- `id` (PK), `costume_id` (FK), `client_id` (FK), `date_debut`, `date_fin`, `prix_total`, `statut`.



---

## 6. Installation et Lancement
1. **Backend** : `flask run` (Python 3.x)
2. **Frontend** : `flutter run`
