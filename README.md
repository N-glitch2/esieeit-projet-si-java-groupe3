# esieeit-projet-si-java-groupe3
Projet SI Java - L2 - 2026-2027 - ESIEE-IT
# Projet SI Java - ESIEE-IT (2026-2027)

## Contexte

Projet de Système d’Information en Java réalisé dans le cadre de la formation L2 à ESIEE-IT.

L’objectif est de construire une application backend organisée, documentée et testée, avec un workflow Git collaboratif.

## Objectifs

- Mettre en place un dépôt Git propre.
- Utiliser Gradle et son wrapper.
- Organiser le code Java avec une structure standard.
- Développer les fonctionnalités du projet par User Stories.
- Ajouter des tests unitaires.
- Travailler en équipe avec GitHub et les Pull Requests.

## Équipe

- Naima role a definir
- deodat a definir 
- brianna a definir 
- emma a definir 

## Stack technique

- Java 21
- Gradle 8.14.3 (wrapper)
- JUnit 5
- Git et GitHub

## Prérequis

- Installer un JDK Java 21.
- Installer Git.
- Utiliser IntelliJ IDEA Community ou un IDE compatible Java.

Gradle n’a pas besoin d’être installé globalement : le projet utilise le Gradle Wrapper.

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

### Lancer l’application

```bash
./gradlew run
```

## Structure du projet

```text
src/
├── main/java/com/esiee/project/
│   └── App.java
└── test/java/com/esiee/project/
    └── AppTest.java
```

## Workflow Git

- `main` : branche stable.
- `develop` : branche d’intégration.
- `feature/...` : branche dédiée à une User Story ou fonctionnalité.

Les fonctionnalités sont développées sur une branche feature puis proposées à `develop` par Pull Request.

## Conventions de commits

Les commits doivent être explicites et suivre une convention de type :

- `chore(init): configure project`
- `docs(readme): update project documentation`
- `test(app): add initial test`
- `feat(auth): add register endpoint`
- `fix(auth): correct login validation`

## Backlog

Les User Stories et les fonctionnalités prévues sont listées dans [`BACKLOG.md`](BACKLOG.md).

