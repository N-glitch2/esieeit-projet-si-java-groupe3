# Projet SI Java - ESIEE-IT (2026-2027)

Projet de Système d'Information en Java - L2 - ESIEE-IT - Groupe 3.

## Contexte

Projet réalisé dans le cadre de la formation L2 à l'ESIEE-IT.
L'objectif est de construire une application backend organisée, documentée et testée, avec un workflow Git collaboratif.

## Le produit

Notre produit permet à un utilisateur de gérer ses projets et ses tâches facilement.
Il vise des étudiants et de petites équipes qui veulent organiser leur travail et suivre son avancement.
Il fournit une API Java sécurisée (inscription, connexion, gestion des projets et des tâches).

### Acteurs

| Acteur | Rôle |
|---|---|
| Visiteur | Non connecté : découvre l'application, crée un compte |
| Utilisateur | Connecté : gère ses projets et ses tâches |
| Admin | Supervise la plateforme (bonus) |

### Fonctionnalités prévues

Le détail complet (user stories, priorités, critères d'acceptation) est dans [`BACKLOG.md`](BACKLOG.md).

| Module | Stories | Priorité principale |
|---|---|---|
| A. Authentification & Profil | US-01 à US-04 | Must / Should |
| B. Gestion des projets | US-05 à US-08 | Must / Should |
| C. Gestion des tâches | US-09 à US-12 | Must / Should |
| D. Recherche / Filtre | US-13, US-14 | Nice |
| E. Administration | US-15 | Nice (bonus) |

**MVP (Must)** : US-01, US-02, US-05, US-06, US-07, US-09, US-10.

## Objectifs pédagogiques

- Mettre en place un dépôt Git propre.
- Utiliser Gradle et son wrapper.
- Organiser le code Java avec une structure standard.
- Développer les fonctionnalités par User Stories.
- Ajouter des tests unitaires.
- Travailler en équipe avec GitHub et les Pull Requests.

## Équipe

| Membre | Rôle |
|---|---|
| Naima | À définir |
| Deodat | À définir |
| Brianna | À définir |
| Emma | À définir |

## Stack technique

- Java 21
- Gradle 8.14.3 (wrapper)
- JUnit 5
- Git et GitHub

## Prérequis

- Installer un JDK Java 21.
- Installer Git.
- Utiliser IntelliJ IDEA Community ou un IDE compatible Java.

Gradle n'a pas besoin d'être installé globalement : le projet utilise le Gradle Wrapper.

## Installation

Cloner le dépôt :

```bash
git clone https://github.com/N-glitch2/esieeit-projet-si-java-groupe3.git
cd esieeit-projet-si-java-groupe3
```

## Exécution

### Lancer les tests

Sur macOS ou Linux :

```bash
./gradlew test
```

Sur Windows :

```bash
gradlew.bat test
```

### Lancer l'application

Sur macOS ou Linux :

```bash
./gradlew run
```

Sur Windows :

```bash
gradlew.bat run
```

## Structure du projet

```text
.
├── BACKLOG.md
├── README.md
└── src/
    ├── main/java/com/esiee/project/
    │   └── App.java
    └── test/java/com/esiee/project/
        └── AppTest.java
```

La structure s'enrichira au fil des User Stories.

## Workflow Git

- `main` : branche stable.
- `develop` : branche d'intégration.
- `feature/...` : branche dédiée à une User Story ou fonctionnalité (ex. `feature/us-01-register`).

Les fonctionnalités sont développées sur une branche feature, puis proposées à `develop` par Pull Request.

## Conventions de commits

Les commits doivent être explicites et suivre une convention de type :

- `chore(init): configure project`
- `docs(readme): update project documentation`
- `docs(backlog): add product backlog`
- `test(app): add initial test`
- `feat(auth): add register endpoint`
- `fix(auth): correct login validation`

## Définition de "Done"

Une User Story est terminée quand :

- le code est OK ;
- les tests sont OK (critères d'acceptation vérifiés) ;
- le README / BACKLOG.md est mis à jour si besoin ;
- la Pull Request est faite vers `develop`.

## Backlog et suivi

- Backlog produit : [`BACKLOG.md`](BACKLOG.md).
- Priorisation MoSCoW : Must / Should / Nice.
- Issues GitHub : une issue par story, avec les labels `must`, `should`, `nice` et `module/auth`, `module/project`, `module/task`, `module/search`, `module/admin`.