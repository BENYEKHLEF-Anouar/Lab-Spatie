---
marp: true
theme: gaia
class: invert
paginate: true
style: |
  @import url('https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;700&family=Roboto:wght@400;700&display=swap');
  section { font-family: 'Roboto', sans-serif; background-color: #1e1e1e; color: #e0e0e0; font-size: 26px; }
  /* Tech Headlines */
  h1, h2, h3 { font-family: 'Roboto', sans-serif; color: #38bdf8; text-transform: uppercase; letter-spacing: 1px; }
  h1 { font-size: 3.5em; text-shadow: 0 0 20px rgba(56, 189, 248, 0.4); }
  blockquote { background: #2d2d2d; border-left: 5px solid #38bdf8; padding: 20px; border-radius: 0 8px 8px 0; }
  .title-info { padding-left:10px; display: inline-block; text-align: left; margin-top: 1rem; font-family: 'JetBrains Mono', monospace; }
  .subtitle { display: block; font-size: 0.6em; color: #94a3b8; text-transform: none; }
  img { border: 2px solid #38bdf8; border-radius: 8px; }

---

# **Présentation: Lab Spatie**
## Gestion des rôles & permissions

<div class="title-info">
  <span class="subtitle">Réalisé par : BENYEKHLEF Anouar</span>
  <span class="subtitle">Encadré par : M. Fouad Essarraj</span>
</div>

---

# Objectif du lab

- **Comprendre** le package Spatie Laravel Permission
- **Gérer** les rôles et les permissions
- **Sécuriser** les fonctionnalités du backend et du frontend
- **Permettre** un contrôle d’accès flexible dans Laravel

---

# C’est quoi Spatie ?

**Spatie Laravel Permission** est un package Laravel qui permet de :

1. Créer des **rôles** (admin, user, etc.)
2. Créer des **permissions** (create, edit, delete…)
3. Associer des permissions aux rôles
4. Vérifier les accès des utilisateurs

> Il facilite la gestion des autorisations de manière dynamique, sans coder des conditions fixes.

---

# Concepts importants

---

### User
- Représente un utilisateur dans l’application.
- Peut avoir plusieurs rôles et permissions.

### Role
- Un groupe de permissions.
- Exemple : Admin, Editor, User.
- Permet de gérer les droits rapidement.

### Permission
- Une action spécifique autorisée.
- Exemple : create post, edit post, delete user.

---

# Architecture (Structure interne)

Le package ajoute une structure relationnelle dans Laravel :

- **roles** → stocke les rôles (Admin, Editor…)
- **permissions** → stocke les permissions (edit, delete…)
- **model_has_roles** → associe un utilisateur à un rôle
- **model_has_permissions** → associe un utilisateur à une permission directe
- **role_has_permissions** → associe un rôle à une ou plusieurs permissions

---

# Fonctionnement

1. Un utilisateur peut avoir **plusieurs rôles**.
2. Un rôle peut avoir **plusieurs permissions**.
3. Les vérifications sont **dynamiques** via la base de données.

---

# Installation de Spatie

**1 - Installer le package via Composer**

```bash
composer require spatie/laravel-permission
```

**2 - Publier la configuration et les migrations**

```bash
php artisan vendor:publish --provider="Spatie\Permission\PermissionServiceProvider"
```

**3 -  Migrer la base de données**

```bash
php artisan migrate
```

---

# Frontend intelligent

Spatie influence aussi l’interface utilisateur :

- **Boutons visibles conditionnels**
  - *Ex : le bouton “Publier” n’apparaît que pour ceux qui ont la permission `publish`.*
- **Liens restreints cachés**
  - *Ex : le lien vers le panneau admin n’apparaît que pour les admins.*

> Évite les clics inutiles et améliore l’expérience utilisateur.

---

# Avantages de Spatie

- Gestion **centralisée** des rôles et permissions
- **Sécurité robuste** et dynamique
- Pas de conditions fixes dans le code
- Compatible avec tous les modèles Laravel
- UI propre et sécurisée
- Modifications possibles sans redéployer le code
