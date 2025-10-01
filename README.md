# DSI2-25-26
Votre demande est claire ! Les ateliers sont déjà en format Markdown. Je vais simplement m'assurer que la présentation finale est optimale en conservant la structure détaillée demandée (Résumé Détaillé, Théorie/Démo, et Exercices Guidés).

Voici la série complète de vos 8 Ateliers de 3 heures en **format Markdown**.

---

## 💻 Atelier 1 : Introduction au Côté Serveur et Bases de PHP (3h)

### Résumé Détaillé des Notions (Leçon Introductive)

* **Environnement de Développement (XAMPP/MAMP/WAMP)** : Pour exécuter du PHP, vous avez besoin d'un serveur HTTP (**Apache**) et d'un interpréteur PHP. Des logiciels comme XAMPP, MAMP ou WAMP simulent un serveur sur votre machine locale. PHP est un langage qui s'exécute **côté serveur**, ce qui signifie qu'il traite les requêtes avant d'envoyer le résultat (du HTML pur) au navigateur du client.
* **Syntaxe de Base** : Le code PHP doit être encapsulé entre les balises `<?php` et `?>`. Les instructions se terminent par un **point-virgule (`;`)**.
    * **Variables** : Déclarées avec le symbole dollar (`$`), elles stockent des données (chaînes de caractères, nombres entiers/flottants, booléens).
    * **Affichage** : Les fonctions **`echo`** et **`print`** sont utilisées pour envoyer du contenu au navigateur.
* **Variables Superglobales (`$_SERVER`)** : Ce sont des tableaux associatifs (clé/valeur) fournis automatiquement par PHP et accessibles de n'importe où. **`$_SERVER`** contient des informations sur le serveur, le chemin du script en cours, et l'environnement de la requête du client (adresse IP, navigateur, etc.).
* **Inclusion de Fichiers (`include` vs. `require`)** : Ces fonctions permettent de réutiliser des blocs de code. **`include`** émet un avertissement si le fichier n'est pas trouvé et continue l'exécution ; **`require`** arrête l'exécution du script, ce qui est souvent préférable pour les fichiers essentiels.

### Théorie & Démonstration (30 min)

1.  **Client vs. Serveur** : Expliquer la différence entre l'exécution JavaScript (client) et PHP (serveur). Montrer la disparition du code PHP dans la source HTML après exécution.
2.  **Démonstration PHP/HTML** : Afficher une variable PHP dans une balise HTML. Montrer une boucle PHP générant des lignes de tableau HTML.
3.  **Présentation de `$_SERVER`** : Afficher quelques clés pour montrer la richesse des informations transmises par le navigateur.

---

### Exercices Pratiques Guidés (2h30)

1.  **Préparation de l'environnement :**
    * Vérifiez que le serveur local est démarré et que vous pouvez accéder à `localhost`.
    * Créez un fichier **`index.php`** dans le dossier de travail.
    * Testez l'affichage d'un simple message (`echo "Hello Server!";`) dans votre navigateur.
2.  **Affichage Dynamique :**
    * Comment utiliser la fonction PHP pour afficher la **date et l'heure actuelles** du serveur sur la page ?
    * Créez une **variable** `$votre_nom` contenant votre nom. Comment l'afficher dans un titre `<h1>` HTML ?
3.  **Exploration des Superglobales :**
    * Comment afficher le **nom du fichier** PHP en cours d'exécution en utilisant la superglobale `$_SERVER` ?
    * Affichez l'**adresse IP du client** (votre machine dans ce cas) en utilisant une clé appropriée de `$_SERVER`.
4.  **Inclusion de Fichiers :**
    * Créez deux fichiers : **`header.php`** (avec le début du HTML et un titre) et **`footer.php`** (avec la fin du HTML et un copyright).
    * Comment utiliser la fonction **`include`** dans `index.php` pour assembler le contenu de ces trois fichiers ?
    * Créez une page **`a_propos.php`** et incluez le `header.php` en utilisant cette fois **`require`**. Quel est l'impact si vous renommez `header.php` en `header_old.php` et tentez d'exécuter `index.php` (include) puis `a_propos.php` (require) ?

---
---

## 💻 Atelier 2 : Gestion des Formulaires et Sécurité de Base (3h)

### Résumé Détaillé des Notions (Leçon Introductive)

* **Traitement des Formulaires (GET et POST)** :
    * **`GET`** : Données ajoutées à l'URL (visibles, utilisées pour la navigation/recherche). Récupérées via **`$_GET`**.
    * **`POST`** : Données envoyées dans le corps de la requête HTTP (invisibles, privilégiées pour les données sensibles ou longues). Récupérées via **`$_POST`**.
* **Validation et Filtrage Côté Serveur** : **C'est une étape cruciale de sécurité.**
    * **Nettoyage (`htmlspecialchars`)** : Toute donnée venant de l'utilisateur et destinée à être affichée doit être **nettoyée** pour empêcher les failles **XSS**. La fonction `htmlspecialchars` convertit les caractères spéciaux pour qu'ils ne soient pas interprétés comme du code.
    * **Filtrage (`filter_var`)** : Utilisé pour vérifier facilement des formats standardisés comme les adresses e-mail.
* **Les Tableaux (Tableaux Associatifs)** : Un **tableau associatif** utilise des chaînes de caractères (clés) au lieu d'indices numériques pour accéder aux valeurs. Ils sont idéaux pour stocker les messages d'erreur (`$erreurs['champ'] = "message"`).

### Théorie & Démonstration (30 min)

1.  **Dangers des Formulaires** : Montrer une faille XSS simple si `htmlspecialchars` n'est pas utilisé.
2.  **`$_POST` vs. `$_GET`** : Afficher la différence de transmission dans l'URL.
3.  **Validation** : Montrer comment utiliser `isset()` et `empty()` pour vérifier un champ requis.

---

### Exercices Pratiques Guidés (2h30)

1.  **Création du Formulaire :**
    * Créez un formulaire HTML simple (dans **`inscription.php`**) avec un champ **Nom**, un champ **Email** et un champ **Mot de passe**.
    * Quel **attribut `method`** du formulaire devez-vous utiliser ? (Utilisez `POST`).
    * L'**attribut `action`** doit pointer vers `inscription.php` lui-même.
2.  **Récupération des Données :**
    * Au début du script PHP, comment vérifiez-vous si le formulaire a été soumis (en testant si `$_POST` existe ou n'est pas vide) ?
    * Comment récupérer la valeur du champ "Email" dans une variable `$email` ?
3.  **Validation Côté Serveur :**
    * Créez un tableau associatif vide nommé `$erreurs`.
    * Comment vérifier si le champ **Nom est vide** ? Si oui, ajoutez un message d'erreur dans le tableau `$erreurs`.
    * Comment utiliser la fonction PHP **`filter_var`** pour valider que la `$email` est bien formatée ? (Si non, ajoutez un message d'erreur).
4.  **Nettoyage et Affichage :**
    * Avant d'afficher l'email ou le nom (même en cas d'erreur), quelle fonction devez-vous appliquer pour la sécurité (`htmlspecialchars`) ?
    * Si le tableau `$erreurs` est **vide** après validation, affichez un message de succès.
    * Sinon, affichez la liste des erreurs dans une liste HTML.

---
---

## 💻 Atelier 3 : Fonctions et Organisation du Code (3h)

### Résumé Détaillé des Notions (Leçon Introductive)

* **Fonctions pour la Modularité (DRY)** : Les fonctions permettent de regrouper des blocs d'instructions réutilisables. C'est le principe **D.R.Y. (Don't Repeat Yourself)**. Elles prennent des arguments, effectuent un traitement, et peuvent retourner une valeur.
* **Portée des Variables (`scope`)** : Les variables définies **à l'intérieur** d'une fonction sont **locales**. La meilleure pratique est de **toujours passer les variables nécessaires en arguments**.
* **Arguments Avancés** :
    * **Arguments par Défaut** : Vous pouvez spécifier une valeur par défaut pour un argument si l'appelant ne le fournit pas.
* **Gestion des Erreurs et Exceptions (`try...catch`)** : Les **exceptions** sont des objets spéciaux représentant des erreurs. Le bloc **`try`** contient le code potentiellement dangereux. Si une exception se produit, l'exécution passe au bloc **`catch`**, permettant de gérer l'erreur proprement sans arrêter le script.

### Théorie & Démonstration (30 min)

1.  **Avantage des Fonctions** : Expliquer DRY et la modularité.
2.  **`global`** : Montrer l'effet de `global` et expliquer pourquoi le passage d'arguments est préférable.
3.  **Exceptions** : Simuler une division par zéro et montrer comment `try...catch` permet de ne pas arrêter l'application.

---

### Exercices Pratiques Guidés (2h30)

1.  **Création d'une Librairie :**
    * Créez un fichier **`fonctions_utils.php`**.
    * Comment inclure ce fichier au début de votre script **`inscription.php`** (Atelier 2) ? (Utilisez `require` car les fonctions sont essentielles).
2.  **Fonction de Validation Générique :**
    * Définissez une fonction **`estChampRequis($valeur)`** qui vérifie si une valeur est non vide et retourne un booléen.
    * **Refactorisation :** Modifiez la validation du nom dans `inscription.php` pour utiliser cette nouvelle fonction.
3.  **Fonction avec Argument par Défaut :**
    * Définissez une fonction **`formaterMessage($texte, $couleur = "noir")`**. Cette fonction doit retourner le texte enveloppé dans une balise `<span>` avec un style CSS pour la couleur.
    * Testez l'appel de la fonction en spécifiant la couleur (ex: "rouge") et sans la spécifier (pour utiliser la valeur par défaut).
4.  **Gestion des Erreurs (Introduction) :**
    * Écrivez une fonction nommée **`diviser(int $a, int $b)`**.
    * Dans cette fonction, utilisez un bloc **`try...catch`** autour de l'opération de division.
    * Si `$b` est zéro, utilisez l'opérateur **`throw new Exception(...)`** pour lancer une exception avec un message clair.
    * Appelez la fonction avec `diviser(10, 0)` et affichez le message d'erreur récupéré dans le bloc `catch`.

---
---

## 💻 Atelier 4 : Introduction à la Base de Données avec MySQL (3h)

### Résumé Détaillé des Notions (Leçon Introductive)

* **Rôle d'une Base de Données (BDD)** : Un système permettant de stocker, d'organiser et de gérer de grandes quantités de données de manière structurée et **persistante**.
* **Concepts du Modèle Relationnel** :
    * **Tables** : Organisation des données (ex: `utilisateurs`, `articles`).
    * **Champs/Colonnes** : Les attributs de la table (ex: `titre`, `email`).
    * **Clé Primaire (`id`)** : Identifiant unique de chaque ligne.
    * **Clé Étrangère** : Établit une relation entre deux tables.
* **Le Langage SQL (Structured Query Language)** : Le langage standard pour interagir avec une BDD. Les opérations **CRUD** sont : **C**reate (`INSERT INTO`), **R**ead (`SELECT`), **U**pdate (`UPDATE`), **D**elete (`DELETE FROM`).
* **PhpMyAdmin** : Interface web graphique utilisée pour administrer et tester les requêtes SQL.

### Théorie & Démonstration (30 min)

1.  **Modèle Relationnel** : Expliquer comment les tables `auteurs` et `livres` seront liées par l'ID.
2.  **Syntaxe SQL** : Montrer et expliquer l'exécution des requêtes `CREATE TABLE` et des exemples `SELECT` simples dans PhpMyAdmin.

---

### Exercices Pratiques Guidés (2h30)

1.  **Préparation de la Base :**
    * Ouvrez **PhpMyAdmin**.
    * Créez une nouvelle base de données nommée **`gestion_bibliotheque`**.
2.  **Conception de la Table `auteurs` :**
    * Écrivez et exécutez la requête SQL pour créer une table **`auteurs`** avec les colonnes : `id` (**clé primaire**, auto-incrémentée), `nom_complet` (VARCHAR 100), `annee_naissance` (INT).
3.  **Conception de la Table `livres` :**
    * Écrivez et exécutez la requête SQL pour créer une table **`livres`** avec les colonnes : `id` (**clé primaire**, auto-incrémentée), `titre` (VARCHAR 255), `annee_publication` (INT), `auteur_id` (INT) - pour lier à la table `auteurs`.
4.  **Insertion de Données (C) :**
    * Écrivez la requête **`INSERT`** pour ajouter deux auteurs fictifs dans la table `auteurs`.
    * Écrivez la requête **`INSERT`** pour ajouter trois livres, en vous assurant que l'**`auteur_id`** des livres correspond aux IDs des auteurs insérés.
5.  **Sélection de Données (R) :**
    * Écrivez la requête **`SELECT`** pour afficher tous les titres des livres et l'année de publication.
    * Écrivez la requête **`SELECT`** pour afficher uniquement le nom de l'auteur ayant l'ID **1**.
    * Écrivez la requête **`SELECT`** pour afficher les livres publiés **après** l'année 2000.

---
---

## 💻 Atelier 5 : Interfaçage PHP et Base de Données (PDO) (3h)

### Résumé Détaillé des Notions (Leçon Introductive)

* **PDO (PHP Data Objects)** : Extension standard et recommandée pour se connecter aux BDD.
* **Connexion** : Création d'un objet `PDO` sécurisé par un bloc `try...catch` avec configuration des erreurs en mode "exception".
* **L'Impératif de Sécurité : Requêtes Préparées** : Séparation de la requête SQL du contenu des variables utilisateurs pour empêcher l'**Injection SQL**.
    * Utilisation de **marqueurs** (`:nom` ou `?`) dans la requête.
    * Utilisation de **`prepare()`** et **`execute()`** pour lier les variables.
* **Exécution et Récupération des Résultats** :
    * **`fetch()`** : Récupère la ligne de résultat suivante.
    * **`fetchAll()`** : Récupère toutes les lignes de résultat.

### Théorie & Démonstration (30 min)

1.  **L'Injection SQL** : Montrer le danger d'une requête non préparée.
2.  **Syntaxe PDO** : Démontrer la connexion et l'utilisation des marqueurs pour une requête `SELECT`.
3.  **Récupération** : Illustrer la différence entre `fetch()` et `fetchAll()` avec une boucle `foreach`.

---

### Exercices Pratiques Guidés (2h30)

1.  **Connexion PDO :**
    * Créez un fichier **`db_config.php`** pour stocker les informations de connexion.
    * Dans un bloc **`try...catch`**, écrivez le code PHP pour créer une nouvelle instance de l'objet **`PDO`**.
    * Configurez PDO pour lancer des **exceptions** en cas d'erreur.
2.  **Lecture de Tous les Livres :**
    * Dans un fichier **`liste_livres.php`**, incluez `db_config.php`.
    * Écrivez la requête SQL pour sélectionner tous les livres.
    * Comment utilisez-vous **`fetchAll()`** pour récupérer toutes les lignes de résultat dans un tableau PHP ?
    * Utilisez une boucle **`foreach`** pour afficher le titre de chaque livre dans une liste HTML.
3.  **Lecture d'un Livre Spécifique (Requêtes Préparées) :**
    * Modifiez l'URL pour passer un paramètre `id` (ex: `liste_livres.php?id=1`). Comment récupérez-vous cette valeur avec **`$_GET`** ?
    * Écrivez la requête SQL **avec un marqueur nommé** (`:id`) pour sélectionner le livre correspondant à cet ID.
    * Comment utilisez-vous la méthode **`prepare()`** puis **`execute()`** pour lier l'ID reçu à votre requête ?
    * Affichez le titre et l'année de publication du livre récupéré via **`fetch()`**.

---
---

## 💻 Atelier 6 : Système CRUD Complet (Créer, Lire, Mettre à Jour, Supprimer) (3h)

### Résumé Détaillé des Notions (Leçon Introductive)

* **Le Cycle de Vie des Données (CRUD)** : Maîtriser les requêtes `INSERT`, `UPDATE`, `DELETE` en PHP/PDO.
* **Redirections Post-Action** : Utilisation de **`header('Location:...')`** après une opération `POST` pour appliquer le modèle **Post-Redirect-Get** et éviter les soumissions multiples.
* **Modification (UPDATE)** : Nécessite de lire l'enregistrement existant (`SELECT WHERE id=X`) pour **pré-remplir** le formulaire avant d'exécuter l'`UPDATE` (avec **`WHERE id = :id`**).

### Théorie & Démonstration (30 min)

1.  **Post-Redirect-Get** : Expliquer pourquoi il faut rediriger après un `POST`.
2.  **Formulaire de Modification** : Montrer comment insérer la valeur existante dans l'attribut `value` d'un champ.

---

### Exercices Pratiques Guidés (2h30)

1.  **Création (C) :**
    * Dans **`creer_livre.php`**, créez le formulaire pour soumettre un nouveau titre, année de publication et `auteur_id`.
    * Une fois soumis, comment utilisez-vous une requête préparée **`INSERT INTO`** pour insérer les données ?
    * Après l'insertion réussie, quelle fonction utilisez-vous pour rediriger l'utilisateur vers **`liste_livres.php`** ?
2.  **Modification (U) :**
    * Créez un lien "Modifier" sur la page de liste qui pointe vers **`modifier_livre.php?id=X`**.
    * Sur cette page, récupérez d'abord les données du livre par son ID et **affichez-les dans les champs `value` du formulaire**.
    * Une fois le formulaire soumis, comment utilisez-vous une requête préparée **`UPDATE`** pour modifier les champs (avec la clause **`WHERE id = :id`** pour cibler l'enregistrement) ?
3.  **Suppression (D) :**
    * Créez un script **`supprimer_livre.php?id=X`**.
    * Dans ce script, comment utilisez-vous la requête préparée **`DELETE FROM`** (avec la clause `WHERE`) ?
    * Après la suppression, redirigez l'utilisateur vers la page de liste.

---
---

## 💻 Atelier 7 : Gestion des Sessions et Espace Membre (3h)

### Résumé Détaillé des Notions (Leçon Introductive)

* **Sessions et État** : Les **sessions** permettent de **maintenir l'état** de l'utilisateur sur plusieurs pages dans un protocole HTTP sans état, en utilisant le tableau **`$_SESSION`**.
* **Sécurité des Mots de Passe** :
    * **Hachage** : Utilisation de **`password_hash`** pour transformer le mot de passe en une chaîne non réversible.
    * **Vérification** : Utilisation de **`password_verify`** pour comparer le mot de passe soumis avec le hachage stocké.
* **Authentification et Contrôle d'Accès** : On vérifie la présence de `$_SESSION['user_id']` pour autoriser l'accès aux zones sécurisées.

### Théorie & Démonstration (30 min)

1.  **Stateless vs. Stateful** : Expliquer le rôle du cookie de session.
2.  **Algorithme de Hachage** : Expliquer pourquoi le hachage est unidirectionnel et l'usage des fonctions PHP natives.

---

### Exercices Pratiques Guidés (2h30)

1.  **Préparation de l'Espace Membre :**
    * Mettez en place un formulaire de connexion simple (**`connexion.php`**).
    * Assurez-vous d'utiliser **`password_hash()`** pour stocker des mots de passe hachés pour vos utilisateurs de test dans la BDD.
2.  **Authentification :**
    * Dans le script de connexion, après avoir récupéré l'utilisateur par son email : comment utilisez-vous **`password_verify()`** pour valider l'accès ?
    * Si la vérification réussit, comment enregistrez-vous l'**ID de l'utilisateur** dans la superglobale **`$_SESSION`** ?
3.  **Contrôle d'Accès (Garde-fou) :**
    * Créez un fichier **`check_auth.php`**. Quel code vérifie si `$_SESSION['user_id']` n'existe pas ?
    * Si l'utilisateur n'est pas connecté, utilisez une redirection pour le renvoyer vers `connexion.php`.
    * **Sécurisation :** Comment incluez-vous **`check_auth.php`** au début des scripts de CRUD (Atelier 6) ?
4.  **Déconnexion :**
    * Créez un script **`deconnexion.php`**.
    * Quelles sont les deux fonctions PHP nécessaires pour **détruire toutes les données de session** et **fermer la session** ?
    * Redirigez l'utilisateur vers la page d'accueil ou de connexion.

---
---

## 💻 Atelier 8 : Programmation Orientée Objet (POO) en PHP (3h)

### Résumé Détaillé des Notions (Leçon Introductive)

* **Classes et Objets** : La **Classe** est le plan, l'**Objet** est l'instance concrète. La POO améliore la structure et la maintenance.
* **Encapsulation** : Masquage des détails internes. Les propriétés sont **`private`** et manipulées par des méthodes publiques appelées **`getter`** (lecture) et **`setter`** (modification).
* **Le Constructeur (`__construct`)** : Méthode automatiquement appelée lors de l'instanciation de l'objet, utilisée pour initialiser les propriétés.
* **Design Pattern : Le Singleton** : Modèle garantissant qu'**une seule instance d'une classe existe** (utilisé pour la connexion BDD).

### Théorie & Démonstration (30 min)

1.  **POO vs. Procédural** : Expliquer les bénéfices de la POO (réutilisation, organisation).
2.  **Classes et Objets** : Montrer l'instanciation (`$objet = new Classe()`) et l'accès aux propriétés/méthodes.

---

### Exercices Pratiques Guidés (2h30)

1.  **Classe de Connexion (Singleton) :**
    * Créez un fichier **`Database.php`** et définissez une **classe `Database`**.
    * Déclarez une propriété statique **`$instance`** (privée).
    * Rendez la méthode **`__construct()`** privée.
    * Définissez une méthode statique **`getInstance()`** qui retourne l'instance PDO unique.
    * **Refactorisation :** Modifiez tous les scripts (Ateliers 5, 6, 7) pour utiliser **`Database::getInstance()`** au lieu de l'ancienne connexion PDO.
2.  **Classe Modèle `Livre` :**
    * Créez un fichier **`Livre.php`** et définissez une **classe `Livre`**.
    * Déclarez les propriétés (`$id`, `$titre`, etc.) comme **privées**.
    * Définissez la méthode **`__construct(array $data)`** et les **`getter`** pour le titre et l'ID.
3.  **Méthode Statique de Récupération :**
    * Dans la classe `Livre`, définissez une méthode statique **`findAll()`**.
    * Cette méthode doit récupérer tous les livres de la BDD via `Database::getInstance()`.
    * Comment utilisez-vous la boucle pour instancier un **nouvel objet `Livre`** pour chaque ligne de la BDD ? (Elle doit retourner un tableau d'objets `Livre`).
    * **Refactorisation :** Modifiez **`liste_livres.php`** pour utiliser `Livre::findAll()` et itérer sur les objets pour afficher les titres.
4.  **Méthode d'Instance (Sauvegarde) :**
    * Dans la classe `Livre`, définissez une méthode publique **`save()`**.
    * Cette méthode doit utiliser `$this->titre` (via les `getter`) pour effectuer l'opération d'**`INSERT`** dans la BDD.
    * Montrez comment créer et sauvegarder un nouveau livre en deux étapes en utilisant cette nouvelle classe.

---
