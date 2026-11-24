# Backlog Produit - Projet SI Java (ESIEE-IT)

## 1. Pitch produit

Notre produit permet à un utilisateur de gérer ses projets et ses tâches facilement, sans outil complexe.
Il vise des étudiants et de petites équipes qui veulent organiser leur travail et suivre son avancement.
Il fournit une API Java sécurisée (inscription, connexion, CRUD projets et tâches) et une interface simple pour l'utiliser.

## 2. Hypothèses et contraintes

- Projet Java (API REST), backlog orienté fonctionnel (pas "faire une base de données").
- MVP réalisable en 9 séances de 3 h.
- Authentification obligatoire (au minimum inscription / connexion).
- Une story doit tenir dans une séance ou moins (sinon elle est découpée).

## 3. Acteurs

| Acteur | Objectifs | Permissions |
|---|---|---|
| Visiteur (non connecté) | Découvrir l'app, créer un compte | Voir la page d'accueil, s'inscrire, se connecter |
| Utilisateur (connecté) | Gérer ses projets et ses tâches | CRUD de ses propres projets et tâches, modifier son profil |
| Admin | Superviser la plateforme | Lister tous les comptes (bonus : bloquer / supprimer) |

## 4. Modules / Features

- **A. Authentification & Profil** : US-01 à US-04
- **B. Gestion des projets** : US-05 à US-08
- **C. Gestion des tâches** : US-09 à US-12
- **D. Recherche / Filtre** : US-13, US-14
- **E. Administration (bonus)** : US-15

## 5. User Stories (MoSCoW + estimation)

Échelle : **S** = 1-2 h, **M** = 3-5 h, **L** = à découper (aucune story L ici).

| ID | Module | User Story | Priorité | Estim. |
|---|---|---|---|---|
| US-01 | Auth | En tant que Visiteur, je veux créer un compte afin de pouvoir accéder à l'application. | Must | M |
| US-02 | Auth | En tant qu'Utilisateur, je veux me connecter afin de retrouver mes projets. | Must | M |
| US-03 | Auth | En tant qu'Utilisateur, je veux me déconnecter afin de sécuriser ma session. | Should | S |
| US-04 | Auth | En tant qu'Utilisateur, je veux modifier mon profil afin de mettre à jour mes informations. | Should | S |
| US-05 | Projets | En tant qu'Utilisateur, je veux créer un projet afin de structurer mon travail. | Must | S |
| US-06 | Projets | En tant qu'Utilisateur, je veux lister mes projets afin de voir tout ce que je gère. | Must | S |
| US-07 | Projets | En tant qu'Utilisateur, je veux modifier un projet afin de corriger ou compléter ses informations. | Must | S |
| US-08 | Projets | En tant qu'Utilisateur, je veux supprimer un projet afin de nettoyer ma liste. | Should | S |
| US-09 | Tâches | En tant qu'Utilisateur, je veux ajouter une tâche dans un projet afin de planifier les actions à faire. | Must | M |
| US-10 | Tâches | En tant qu'Utilisateur, je veux changer le statut d'une tâche afin de suivre l'avancement. | Must | S |
| US-11 | Tâches | En tant qu'Utilisateur, je veux modifier une tâche afin d'ajuster son contenu. | Should | S |
| US-12 | Tâches | En tant qu'Utilisateur, je veux supprimer une tâche afin d'enlever les tâches inutiles. | Should | S |
| US-13 | Recherche | En tant qu'Utilisateur, je veux filtrer les tâches par statut afin de me concentrer sur les tâches urgentes. | Nice | S |
| US-14 | Recherche | En tant qu'Utilisateur, je veux rechercher une tâche par mot-clé afin de retrouver rapidement une information. | Nice | M |
| US-15 | Admin | En tant qu'Admin, je veux lister tous les utilisateurs afin de surveiller la plateforme. | Nice | S |

### Répartition MoSCoW

- **Must (MVP)** : US-01, US-02, US-05, US-06, US-07, US-09, US-10
- **Should (après le socle)** : US-03, US-04, US-08, US-11, US-12
- **Nice (selon l'avancement)** : US-13, US-14, US-15

## 6. Critères d'acceptation

### Module A - Authentification & Profil

#### US-01 - Créer un compte

- **Succès**
  - Given je suis sur la page d'inscription
  - When je saisis un email valide (test@example.com) et un mot de passe conforme (8 caractères min.)
  - Then mon compte est créé et je suis redirigé vers la page de connexion
- **Email déjà utilisé**
  - Given un compte existe déjà avec l'email test@example.com
  - When je tente de m'inscrire avec le même email
  - Then je reçois le message "Email déjà utilisé" et aucun compte n'est créé
- **Mot de passe trop court**
  - Given je suis sur la page d'inscription
  - When je saisis un mot de passe de 5 caractères
  - Then je reçois le message "Le mot de passe doit contenir au moins 8 caractères"
- **Email invalide**
  - Given je suis sur la page d'inscription
  - When je saisis un email mal formé (ex. "test@")
  - Then je reçois une erreur claire et le compte n'est pas créé

#### US-02 - Se connecter

- **Succès**
  - Given j'ai un compte existant
  - When je saisis mon email et mon mot de passe corrects
  - Then je suis connecté et j'accède à la liste de mes projets
- **Identifiants incorrects**
  - Given j'ai un compte existant
  - When je saisis un mauvais mot de passe
  - Then je reçois le message "Identifiants invalides" et je reste déconnecté
- **Accès protégé**
  - Given je ne suis pas connecté
  - When je tente d'accéder à mes projets
  - Then l'accès est refusé (401 ou redirection vers la connexion)

#### US-03 - Se déconnecter

- **Succès**
  - Given je suis connecté
  - When je clique sur "Se déconnecter"
  - Then ma session est terminée et je reviens à la page de connexion
- **Session invalidée**
  - Given je viens de me déconnecter
  - When j'essaie d'utiliser mon ancien jeton / ma session
  - Then l'accès est refusé

#### US-04 - Modifier mon profil

- **Succès**
  - Given je suis connecté
  - When je modifie mon nom et j'enregistre
  - Then la modification est sauvegardée et visible à la prochaine consultation
- **Champ invalide**
  - Given je suis sur mon profil
  - When je saisis un nom vide
  - Then je reçois une erreur et rien n'est modifié
- **Email déjà pris**
  - Given un autre compte utilise l'email X
  - When je tente de changer mon email pour X
  - Then la modification est refusée avec un message explicite

### Module B - Gestion des projets

#### US-05 - Créer un projet

- **Succès**
  - Given je suis connecté
  - When je crée un projet avec un nom valide
  - Then le projet est créé, m'appartient et apparaît dans ma liste
- **Nom manquant**
  - Given je suis connecté
  - When je crée un projet sans nom
  - Then je reçois une erreur de validation et aucun projet n'est créé
- **Non connecté**
  - Given je ne suis pas connecté
  - When je tente de créer un projet
  - Then l'accès est refusé

#### US-06 - Lister mes projets

- **Succès**
  - Given je suis connecté et j'ai 3 projets
  - When j'ouvre la liste de mes projets
  - Then je vois mes 3 projets
- **Liste vide**
  - Given je suis connecté et je n'ai aucun projet
  - When j'ouvre la liste
  - Then je vois un message "Aucun projet" et non une erreur
- **Isolation des données**
  - Given un autre utilisateur possède des projets
  - When j'ouvre ma liste
  - Then je ne vois que mes propres projets

#### US-07 - Modifier un projet

- **Succès**
  - Given je possède un projet
  - When je modifie son nom et j'enregistre
  - Then la modification est persistante
- **Validation**
  - Given je modifie un projet
  - When je saisis un nom vide
  - Then la modification est refusée avec un message d'erreur
- **Projet d'un autre**
  - Given un projet appartient à un autre utilisateur
  - When j'essaie de le modifier
  - Then l'accès est refusé (403 ou 404)

#### US-08 - Supprimer un projet

- **Succès**
  - Given je possède un projet
  - When je le supprime
  - Then il n'apparaît plus dans ma liste
- **Cascade**
  - Given le projet contient des tâches
  - When je le supprime
  - Then ses tâches sont également supprimées (ou une confirmation me prévient)
- **Projet d'un autre**
  - Given un projet appartient à un autre utilisateur
  - When j'essaie de le supprimer
  - Then l'accès est refusé

### Module C - Gestion des tâches

#### US-09 - Ajouter une tâche

- **Succès**
  - Given je suis connecté
  - When je crée une tâche dans un projet existant
  - Then la tâche apparaît dans la liste et est associée au bon projet
- **Statut par défaut**
  - Given je crée une tâche sans préciser de statut
  - When elle est enregistrée
  - Then son statut est "À faire"
- **Projet inexistant**
  - Given je cible un projet qui n'existe pas
  - When je crée une tâche
  - Then je reçois une erreur (404) et aucune tâche n'est créée
- **Titre manquant**
  - Given je crée une tâche
  - When le titre est vide
  - Then je reçois une erreur de validation

#### US-10 - Changer le statut d'une tâche

- **Succès**
  - Given j'ai une tâche "À faire"
  - When je la passe à "En cours"
  - Then son statut est mis à jour et persistant
- **Statut invalide**
  - Given j'ai une tâche
  - When je demande un statut inconnu (ex. "Terminé-ish")
  - Then la requête est refusée avec un message listant les statuts valides
- **Tâche d'un autre**
  - Given une tâche appartient au projet d'un autre utilisateur
  - When j'essaie de changer son statut
  - Then l'accès est refusé

#### US-11 - Modifier une tâche

- **Succès**
  - Given j'ai une tâche existante
  - When je modifie son titre ou sa description
  - Then les changements sont enregistrés
- **Validation**
  - Given je modifie une tâche
  - When le titre devient vide
  - Then la modification est refusée

#### US-12 - Supprimer une tâche

- **Succès**
  - Given j'ai une tâche existante
  - When je la supprime
  - Then elle n'apparaît plus dans la liste du projet
- **Tâche inexistante**
  - Given la tâche a déjà été supprimée
  - When je tente de la supprimer à nouveau
  - Then je reçois une erreur 404

### Module D - Recherche / Filtre

#### US-13 - Filtrer par statut

- **Succès**
  - Given un projet contient des tâches "À faire" et "Terminé"
  - When je filtre sur "À faire"
  - Then seules les tâches "À faire" sont affichées
- **Aucun résultat**
  - Given aucune tâche n'a le statut choisi
  - When j'applique le filtre
  - Then je vois un message "Aucune tâche"

#### US-14 - Rechercher par mot-clé

- **Succès**
  - Given j'ai une tâche "Écrire le rapport"
  - When je recherche "rapport"
  - Then la tâche apparaît dans les résultats
- **Insensible à la casse**
  - Given j'ai une tâche "Écrire le rapport"
  - When je recherche "RAPPORT"
  - Then la tâche apparaît toujours
- **Aucun résultat**
  - Given aucune tâche ne contient le mot recherché
  - When je lance la recherche
  - Then je vois un message "Aucun résultat"

### Module E - Administration (bonus)

#### US-15 - Lister tous les utilisateurs

- **Succès**
  - Given je suis connecté en tant qu'Admin
  - When j'ouvre la liste des utilisateurs
  - Then je vois tous les comptes (sans leurs mots de passe)
- **Accès interdit**
  - Given je suis un Utilisateur simple
  - When j'essaie d'accéder à cette liste
  - Then l'accès est refusé (403)

## 7. Règles transverses (sécurité)

- Accès interdit si l'utilisateur n'est pas connecté.
- Un utilisateur ne voit ni ne modifie jamais les données d'un autre utilisateur.
- Les mots de passe ne sont jamais stockés en clair ni renvoyés par l'API.

## 8. Hors périmètre (cette itération)

- Notifications par email, mode sombre, dashboard avec graphiques.
- Partage de projets entre utilisateurs, rôles par projet.
- Blocage / suppression de comptes par l'Admin (extension de US-15).

## 9. Définition de "Done" (DoD)

Une story est terminée quand :

- le code est OK ;
- les tests sont OK (critères d'acceptation vérifiés) ;
- le README / BACKLOG.md est mis à jour si besoin ;
- la PR est faite vers `develop`.

## 10. Organisation sur la plateforme (optionnel)

- Une issue GitHub/GitLab par story (template ci-dessous).
- Labels de priorité : `must`, `should`, `nice`.
- Labels de module : `module/auth`, `module/project`, `module/task`, `module/search`, `module/admin`.
- Board : To do / Doing / Done.
