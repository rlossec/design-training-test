# Conception technique

# Table des matières

- [1. Architecture Système](#1-architecture-systeme)
  - [1.1. Schéma global](#11-schema-global)

---

## 1. Architecture Système

### 1.1. Schéma global

```
┌─────────────────────────────────────────────────────────────────┐
│                           FRONTEND                              │
├─────────────────────────────────────────────────────────────────┤
│  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐  │
│  │ Portail citoyen │  │  Portail Agent  │  │  Portail Admin  │  │
│  └─────────────────┘  └─────────────────┘  └─────────────────┘  │
└─────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────┐
│                        BACKEND LAYER                            │
├─────────────────────────────────────────────────────────────────┤
│               ┌──────────────────────────────────┐              │
│               │          Authentication          │              │
│               ├──────────────────────────────────┤              │
│               │         Authentication           │              │
│               │    Intégration FranceConnect     │              │
│               └──────────────────────────────────┘              │
│                                                                 │
│               ┌──────────────────────────────────┐              │
│               │            Procedures            │              │
│               ├──────────────────────────────────┤              │
│               │               Quest              │              │
│               │               Reward             │              │
│               │              Documents           │              │
│               └──────────────────────────────────┘              │
│                                                                 │
│               ┌──────────────────────────────────┐              │
│               │          User Progress           │              │
│               ├──────────────────────────────────┤              │
│               │           XP Progression         │              │
│               │              Habits              │              │
│               │           Customization          │              │
│               └──────────────────────────────────┘              │
│                                                                 │
│               ┌──────────────────────────────────┐              │
│               │           AI Assistant           │              │
│               ├──────────────────────────────────┤              │
│               │            ChatBot AI            │              │
│               │       Action Recommandation      │              │
│               └──────────────────────────────────┘              │
│                                                                 │
│               ┌──────────────────────────────────┐              │
│               │             Social               │              │
│               ├──────────────────────────────────┤              │
│               │             Entraide             │              │
│               │             Partage              │              │
│               └──────────────────────────────────┘              │
│                                                                 │
│               ┌──────────────────────────────────┐              │
│               │          Intégrations            │              │
│               ├──────────────────────────────────┤              │
│               │             Passport             │              │
│               │               Taxes              │              │
│               │              Address             │              │
│               └──────────────────────────────────┘              │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
                                │
┌─────────────────────────────────────────────────────────────────┐
│                          DATABASE                               │
├─────────────────────────────────────────────────────────────────┤
│            ┌─────────────────┐  ┌─────────────────┐             │
│            │   PostgreSQL    │  │   Redis Cache   │             │
│            └─────────────────┘  └─────────────────┘             │
└─────────────────────────────────────────────────────────────────┘
                                │
┌─────────────────────────────────────────────────────────────────┐
│                          IA LAYER                               │
├─────────────────────────────────────────────────────────────────┤
│            ┌─────────────────┐  ┌─────────────────┐             │
│            │       LLM       │  │      RecSys     │             │
│            └─────────────────┘  └─────────────────┘             │
└─────────────────────────────────────────────────────────────────┘
                                │
┌─────────────────────────────────────────────────────────────────┐
│                      EXTERNAL SERVICES                          │
├─────────────────────────────────────────────────────────────────┤
│       ┌─────────────────┐           ┌─────────────────┐         │
│       │   FranceConnect │           │   APIs Gouv     │         │
│       └─────────────────┘           └─────────────────┘         │
└─────────────────────────────────────────────────────────────────┘
```

### 1.2. Description des modules

1. **Authentification**

Responsabilités :

- Information utilisateur, mot de passe haché
- Gestion des permissions et rôles

2.  **Intégration FranceConnect**

Responsabilités :

- Communication avec FranceConnect
- Gestion des JWT

3. **Quest**

Responsabilités :

- Gestion des démarches et étapes
- Suivi de l’état (progression, sauvegarde étape par étape)
- Gestion des documents

4. **Module récompenses**

Responsabilités :

- Gestion des badges et Récompenses

5. **XP Progression**

Responsabilités :

- Gestion de l'expérience et des niveaux
- Gestion des titres
- Classement (V2)

6. **Habits**

Responsabilités :

- Enregistrement des interactions avec le site (-> Module RecSys)
- Calcul intelligent des délais ?

7. **Personnalisation**

- **Profils utilisateur** : Customisation de l'avatar et des préférences
- **Notifications** : Système d'alertes personnalisables
- **Tableau de bord** : Interface personnalisée selon les besoins

8. **Chatbot**

Responsabilités :

- Gestion des discussions, en consommant le LLM
- Sauvegarde des conversations

9. **Action recommandation**

- Gestion des Recommandations en consommant le modèle (RecSys)
- Notifications

10. **Social**

Responsabilités :

- Partage d'accomplissements
- Entraide communautaire

11. **Module LLM**

Responsabilités :

- Construction du LLM fine-tuné

12. **Module RecSys**

Responsabilités :

- Pipeline
- Segmentation des utilisateurs
- Calcul des délais
