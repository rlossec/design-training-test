# Note de Cadrage

Ce document présente la vision, les objectifs business et l’analyse fonctionnelle pour la création d’un portail web ludique et centralisé visant à simplifier et rendre plus gratifiantes les démarches administratives.

Il détaille le périmètre du MVP, les fonctionnalités prioritaires, les risques identifiés ainsi que leur mitigation.

---

# Table des matières

- [1. Executive Summary](#1-executive-summary)
  - [1.1. Vision produit](#11-vision-produit)
  - [1.2. Objectifs business](#12-objectifs-business)
  - [1.3.Proposition de valeur](#13-proposition-de-valeur)
- [2. Questions Critiques](#2-questions-critiques)
- [3. Analyse MVP](#3-analyse-mvp)
  - [3.1. Fonctionnalités core](#31-fonctionnalités-core)
  - [3.2. Matrice effort/valeur](#32-matrice-effortvaleur)
  - [3.3. Timeline proposée](#33-timeline-proposée)
  - [3.4. Features à reporter](#34-features-à-reporter)
- [4. Risques Majeurs & Mitigation](#4-risques-majeurs--mitigation)
  - [4.1. Risques principaux](#41-risques-principaux)
  - [4.2. Autres risques](#42-autres-risques)

---

## 1. Executive Summary

### 1.1. Vision produit

Créer un portail web **ludique et centralisé** qui simplifie les démarches administratives et les rend plus gratifiantes. La plateforme s’adapte au profil et aux besoins des utilisateurs afin de réduire la complexité perçue, fluidifier les processus et encourager l’achèvement des démarches.

### 1.2. Objectifs business

- **Simplifier l’expérience administrative** en réduisant la complexité et le temps passé par les citoyens.
- **Réduire les abandons et erreurs** dans la réalisation des démarches grâce à un accompagnement guidé et motivant.
- **Favoriser l'entraide et l'émulation** pour les démarches administratives.

### 1.3. Proposition de valeur

Un portail unique qui transforme les démarches administratives en parcours clairs et engageants. En combinant simplification, mécaniques ludiques et entraide, la plateforme aide chaque citoyen à progresser efficacement dans ses démarches, tout en garantissant fiabilité, sécurité et accessibilité.

## 2. Questions Critiques

| Top | Question                                                                                                                                                                                                                                       | Impact       | Justification                                                                                |
| --- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | -------------------------------------------------------------------------------------------- |
| 1   | Quelles types de démarches envisagez vous, quelles seraient les démarches prioritaires à intégrer ?                                                                                                                                            | Bloquant     | Les démarches définissent le périmètre fonctionnel et conditionne tout le cadrage du projet. |
| 2   | Au delà des Personas, en terme de permissions, on peut distinguer deux types de personnes pourront interagir avec l’interface, des client et des agents. Auth France Connect serait aussi configuré pour les agents ?                          | Important    | Anticipation de la nécessité d'accès et de portail différent selon le profil                 |
| 3   | Prévoyez vous de faire une segmentation des clients de la phase de test pour définir des profils utilisateurs ou avez vous des profils fixés, ou faut il les définir ?                                                                         | Important    | Conditionne les premiers choix d'implémentation                                              |
| 4   | Quel niveau de personnalisation est attendu pour l’assistant intelligent dès la version initiale ?                                                                                                                                             | Important    | La complexité technique dépend du niveau attendu (guidage simple vs apprentissage).          |
| 5   | Au sujet de la gratification lorsque le citoyenne réalise des tâches, vous évoquer des avantages spécifiques selon les réalisations. Avez vous des exemple d’avantages en tête ?                                                               | Important    | Clarifie la valeur réelle des récompenses et leur faisabilité.                               |
| 6   | Concernant les dynamiques de groupe, quel périmètre d’interaction est envisagé (amis, famille, communauté élargie) ?                                                                                                                           | Important    | La conception dépend du niveau de partage attendu et des règles de confidentialité.          |
| 7   | Doit on limiter les aidant parmi un groupe d’agent ou deux citoyens pourraient s’entraider avec autorisation de l’aidé                                                                                                                         | Important    | Détermine de périmètre d'une feature avancée                                                 |
| 8   | Chaque personne configure l’accès à ses informations, badges, mais prévoyez vous des limitations, par exemple selon le profil utilisateur. Par exemple un utilisateur ne pourrait donner des accès qu’à des agents, personnes agrées, famille. | Important    | Conditionne l'architecture des droits et permissions                                         |
| 9   | Y a-t-il des frameworks qui sont privilégiés dans les différentes intégrations, par exemple sur les services prioritaires ?                                                                                                                    | Important    | Conditionne les choix des technologies utilisées                                             |
| 10  | Quelle différence fonctionnelle faites-vous entre les « badges » et les « titres » ?                                                                                                                                                           | Nice-to-have | Clarifie ou Évite les redondances fonctionnelles et précise la logique de gamification.      |

## 3. Analyse MVP

### 3.1. Fonctionnalités core

#### 3.1.1. Authentification via FranceConnect

- **Rôle** : Permet à l’utilisateur de se connecter de manière sécurisée avec son identité numérique déjà reconnue.

- **Pourquoi MVP** : Contrainte légale et technique pour pouvoir utiliser les services administratifs.

- **Livrables attendus** :
  - Connexion/déconnexion avec FranceConnect
  - Gestion des erreurs de login
  - Redirection vers le dashboard après connexion

#### 3.1.2. Profil utilisateur

- **Rôle** : Point central de personnalisation et de suivi de l’utilisateur.

- **Pourquoi MVP** : Base indispensable pour enregistrer progression, préférences et historique. Elle peut aussi permettre une première étape de personnalisation de l'aide.

- **Contenu minimal** :
  - Informations de base (nom, email, avatar éventuel)
  - Historique des démarches réalisées
  - Stockage du niveau/XP
  - Placeholder, avec Choix parmi une liste de profil :
    - Basique
    - Aide légère
    - Aide avancée
    - Professionnel
    - Expert

#### 3.1.3. Dashboard évolutif

- **Rôle** : Interface d’accueil centralisée affichant l’état des démarches et la progression.

- **Pourquoi MVP** : C’est le cœur de l’expérience utilisateur en donnant une vue simple et motivante.

- **Contenu minimal** :
  - Liste des démarches en cours/à faire
  - Indicateurs de progression visuels (barres d’avancement, % réalisé)
  - Accès rapide au profil et à l’historique

#### 3.1.4.Découpage des démarches

- **Rôle** : Transformation des démarches administratives en étapes simples, guidées.

- **Pourquoi MVP** : Différenciateur majeur du produit par la réduction de la complexité perçue.

- **Contenu minimal** :
  - 3 démarches prioritaires découpées en étapes claires : Passeport, Déclaration d'impôt et Changement d'adresse
  - Affichage étape par étape avec validation/sauvegarde

#### 3.1.5. Expérience, niveaux et classement

- **Rôle** : Introduire un premier élément de gamification légère.

- **Pourquoi MVP** : Simple à développer, différenciateur fort par rapport à une plateforme administrative classique.

- **Contenu minimal** :
  - Système de points basé sur l’avancement des démarches
  - Attribution automatique de niveaux
  - Classement individuel visible dans le profil (pas encore social ou compétitif)

### 3.2. Matrice effort/valeur

| **Feature**                       | **Valeur** | **Effort** | **Position**     |
| --------------------------------- | ---------- | ---------- | ---------------- |
| Authentification FranceConnect    | 5          | 5          | MVP              |
| Profil utilisateur (évolutif)     | 5          | 3          | MVP              |
| Dashboard (évolutif)              | 5          | 3          | MVP              |
| Découpage des démarches           | 5          | 4          | MVP              |
| Expérience, niveaux et Classement | 3          | 2          | MVP              |
| Notifications                     | 4          | 2          | Reporter (V2)    |
| Badges et récompenses             | 4          | 2          | Reporter (V2)    |
| Assistant intelligent             | 4          | 5          | Reporter (V2)    |
| Entraide entre citoyens           | 3          | 5          | Reporter (V2)    |
| Accès agent (administration)      | 3          | 5          | Reporter (V2/V3) |
| Paiement                          | 2          | 5          | Reporter (V3)    |

### 3.3 Timeline proposée

- **Sprint 1 (Semaines 1-3)**
  - **Mise en place de l'environnement** : Hébergement, base de données, outils de développement.
  - **Développement de l'authentification** : Intégration de FranceConnect.
  - **Développement du profil utilisateur** : Modèle de données et interface de base.
- **Sprint 2 (Semaines 4-6)**
  - **Développement d'une des démarches prioritaires découpées** : Création des quêtes pour les Passeports.
  - **Création de l'interface du tableau de bord** : Affichage des quêtes, placeholder pour l'expérience et niveau selon leur avancement
- **Sprint 3 (Semaines 7-9)**
  - **Développement des autres démarches prioritaires découpées** : Création des quêtes complète pour les impôts puis les adresses.
  - **Finalisation du système de level et expérience**
  - **Tests et retours utilisateurs** : Tester l'ensemble du MVP avec le groupe restreint et collecter les retours pour la V2.

### 3.4. Features à reporter

**1. Notifications**

Les notifications email ou sur l'application sont à forte valeur pour l'implication mais non indispensable au lancement.

**2. Badges et récompenses**

Ces éléments de gamification plus poussée, pourrait être introduit après premiers retours utilisateurs sur les démarches, pour ne pas trop complexifié dans un premier temps.

**3. Assistant intelligent**
Si la valeur ajoutée est importante il nécessite du temps de R&D pour sa forme simple et des risques de RGPD et de confientialité pour une forme avancée.

**4. Entraide entre citoyens**

De même, l'utilité pour des personnes isolées ou éloigné du numérique serait grande mais les risques semblent trop élévé et doivent être bien défini et prévenu avant toute implémentation.

**5. Accès agent (administration)**

L'apport n'est pas central dans un premier temps et pourrait être complexe en terme d'intégration.

**6. Paiement**

Secondaire, les démarches prioritaires ne nécessite pas de paiement, l'implémentation complexe également.

## 4. Risques Majeurs & Mitigation

### 4.1. Risques principaux

**1. Adoption utilisateur limitée**

Le coeur du projet est d'impliqué le citoyen, cela n'est pas garanti. Cela est aussi très dépendant du profil des citoyens. Leur segmentation sera clé pour la réussite globale.

**Mitigation**

- Intégrer la gamification légère dès le MVP
- Bien définir les profils utilisateurs initiaux et les faire évoluer progressivement
- Rendre le profil paramétrable par l'utilisteur dans un second temps
- Organiser des tests utilisateurs dès le MVP

**2. Confidentialité & partage des données**

Les données administratives selon les services peuvent être hautement sensibles. Plusieurs features rendent le problème encore davantage sensible :

- le classement
- l'entraide
- les quêtes collectives
- l'assistant intelligent

**Mitigation**

- Définir le périmètre des données partagées dès la conception
- Prévoir une configuration utilisateur pour la visibilité
- Limiter les classements à un usage individuel au départ

**3. Dépendance aux API des services adminsitratifs**

Les services des différentes démarches administratives peuvent être soumis à des contraintes diverses. Chacune des intégrations pourra être un défi, en développement mais aussi en production

**Mitigation**

- Identifier tôt les systèmes des démarches prioritaires et leurs contraintes
- Prévoir des connecteurs modulaires et évolutifs
- Prioriser et reporter l’intégration complexe en V2/V3

### 4.2. Autres risques

**Intégration FranceConnect**

- Impliquer tôt les équipes FranceConnect
- Prévoir un fallback temporaire pour tester le reste du MVP.

**Complexité réglementaire (RGPD, paiement)**

- Anticiper un audit juridique dès la phase de cadrage
- Prioriser la mise en conformité RGPD dès la conception
- Reporter le paiement sécurisé en V3

## 5. Approche Recommandée

In progress

### Méthodologie suggérée

In progress

### Équipe minimale

In progress

### Quick wins

In progress

### Next steps

In progress

## Bonus

### Architecture

In progress
