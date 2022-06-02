# Spécifications

***Créé le: 5/12/2020***
~
***Mis à jour le: 5/12/2020***


## I. Introduction
Depuis plusieurs années, le nombre de personnes ayant un ou plusieurs animaux augmente de plus en plus.
Cela est d'autant plus vrai pour les NACs, notamment les reptiles et amphibiens.

Il est parfois compliqué de pouvoir suivre correctement ses animaux, que ce soit avec un seul ou plusieurs centaines.

## II. Objectifs
### 1. Résumé

Depuis plusieurs années, le nombre de personnes ayant un ou plusieurs animaux augmente de plus en plus.
Cela est d'autant plus vrai pour les nouveaux animaux de compagnie (NAC*), dont font parties les reptiles et amphibiens.
Il est parfois compliqué de pouvoir suivre correctement ses animaux, que ce soit avec un seul ou plusieurs centaines.

Her Pet est une application qui a pour vocation de réunir la communauté qui s’intéresse à l’élevage et au suivi des reptiles en leur permettant d'enregistrer leurs animaux en y ajoutant toutes les informations nécessaires comme le suivi général quotidien, l'alimentation, l'état de santé, les soins, et autres observations importantes.
 
En effet, chacun pourra suivre la fiche de l’animal à travers un carnet de santé en ligne qui permettra d’avoir un regard global au niveau de sa santé, de son alimentation ou de son environnement.

**NAC: Les Nouveaux Animaux de Compagnie concerne les animaux qui peuvent êtres élevés en captivité mais ne faisant pas partie des chats et chiens*

### 2. Maquette

### 3. Choix techniques:
  ***A confirmer***
- Mobile: React Native
- Front-End: React
- Back-End: NodeJS, ExpressJS, Sequelize (ORM), MariaDB(SQL)

## III. Périmètre
Ce logiciel est à l'attention des personnes souhaitant avoir un suivi centralisé, informatisé, complet et exhaustif de leurs animaux.
Il sera accessible sur ordinateur, tablette et téléphone en ligne ou hors-ligne.

## IV. Fonctionnalités

### Accessibilité
- Accessibilité multi-plateformes.
- Choix de langue: FR - EN.

### Authentification
- Un utilisateur peut s'enregistrer, se connecter, modifier ses informations de compte et supprimer son compte.
- Un utilisateur doit être connecté pour utiliser les fonctionnalités.
- Un utilisateur enregistré/connecté est un éleveur.

### Animaux & Co
- Un éleveur peut ajouter, modifier ou supprimer un animal (qui lui est lié).
- Un éleveur peut voir l'ensemble de ses animaux avec leurs informations (+ fiches associées) : Cheptel.
- Une fiche de suivi du nourrissage se crée en même temps que celle d'un animal, qui lui est associé.
- Un éleveur peut modifier la fiche de nourrissage.
- Un carnet de santé se crée en même temps que celle d'un animal, qui lui est associé.
- Le carnet de santé peut être enregistrer au format PDF.
- Une fiche de suivi du rapport taille/poids se crée en même temps que celle d'un animal, qui lui est associé.
- Un éleveur peut ajouter, modifier ou supprimer la fiche d'une installation.
- Un éleveur peut lier une installation à un ou plusieurs animaux.
- Un éleveur peut créer, modifier ou supprimer la fiche de reproduction d'un animal.
- Un éleveur peut créer ou modifier un événement lié à l'installation ou à l'animal

### Autres
- Page d'accueil globale.
- Tableau de bord individuel.
- FAQ animaux, symptômes, conseils, etc. (évolutive)
- Module de recherche (par nom ou identifiant d'application)

### Fonctionnalités possibles (évolutions futures)
- QRcode (génération + scan pour accéder en temps réel à la fiche de l'installation et animaux)
- Envoi du carnet de santé complet au vétérinaire directement par mail
- Registre entrées-sorties
- Transferts d'animaux entre éleveurs.
- Forum communautaire et transactionnel.
- Classification intégrée.
- Graphiques d'ensemble des données par espèce, visible par tous les éleveurs.
- Calendrier de suivi (global)
- Carte avec les éleveurs de l'appli (ex: Géolocalisation en temps réel + avec paramètre de compte correspondant)
- Suivre un autre éleveur (notifications lors d'événements particuliers, paramétrable)
- Notifications d'événements (nourrissages, rendez-vous véto, etc)
- Ajouter un événement de nourrissage à tous les animaux d'une même installation
- Affichage des conditions météo (T°C, %, précipitations) en temps réels du pays d'origine de l'animal (à préciser dans le cas de plusieurs)
- Mise en contact des éleveurs entre eux
- Suivi des traintements

## V. Dictionnaire de données

- App_ID :
    * Chaîne de caractères (255)
    * [Eleveur, Animal]
    * Génération automatique et aléatoire à la création de l'Entité.
    * Unique
    * Requis

- Age :
    * Entier >=0
    * [Animal, Eleveur]
    * Calcul automatique via date de naissance.
    * Requis [Animal] - Facultatif [Eleveur]

- Capacitaire :
    * Entier (0, 1, 2)
    * [Eleveur]
    * Choix unique
        * 0 : Non
        * 1 : En cours
        * 2 : Oui
    * Requis

- CDC :
    * Booléen
    * [Animal]
    * Choix
        * false : Non / Non renseigné
        * true : Oui
    * Requis

- Email :
    * Chaîne de caractère (120)
    * [Eleveur]
    * Format Email valide
    * Unique
    * Identifiant de connexion
    * Requis

- Nom :
    * Chaîne de caractère (120)
    * [Animal]
    * Facultatif

- Nom Scientifique :
    * Chaîne de caratères (120)
    * [Animal]
    * Requis

- Nom Vernaculaire :
    * Chaîne de caratères (120)
    * [Animal]
    * Facultatif

- Origine :
    * Entier (0, 3)
    * [Animal]
    * Choix
        * 0 : NC (Né en Captivité)
        * 1 : Capturé en milieu naturel
        * 2 : Ferme d'élevage
        * 3 : Inconnue
    * Requis

- Photo :
    * Chaîne de caractère
    * Facultatif

- Pseudo :
    * Chaîne de caratère
    * [Eleveur]
    * Unique
    * Facultatif

- Sexe :
    * Entier (0, 2)
    * [Animal]
    * Choix
        * 0 : Indéterminé
        * 1 : Mâle
        * 2 : Femelle
    * Obligatoire

- Taille :
    * Décimal (cf. Unite_Taille)
        * cm : (0, 300)
        * m : (0, 9)
    * [Animal, Nourriture]
    * Facultatif

- Unite_Taille :
    * Booléen
    * [Animal, Nourriture]
    * Choix:
        * 0 : cm
        * 1 : m
    * Facultatif (sauf si **Taille** renseignée)

## VI. Fonctionnalités détaillées

### 1. Compte 

- Je dois valider un captcha
    * Lorque je m'inscris
    * Lorsque je me connecte
- Je peux m'authentifier
    * Avec un email et un mot de passe
    * Avec Google
    * Avec Facebook
    * une fois authentifié, je suis redirigé vers la page de connexion
- Je peux me connecter
    * Avec mon email ou mon pseudo (si il existe) et mon mot de passe
    * Avec mon compte Google
    * Avec mon compte Facebook
    * Redirection sur la page de compte
- Je peux me déconnecter
    * Bouton de déconnexion
    * Redirection sur page d'accueil
- Je peux récupérer mon mot de passe via mon email
    * Envoi email de récupération
    * Redirection vers page de modification de mot de passe

### 2. Paramètres de compte

- Je peux modifier mes paramètres de compte si je suis connecté
- Je peux modifier ma visibilité aux autres éleveurs
    * Je peux me rendre visible
    * Je peux me rendre invisible (valeur par défaut)
- Je peux modifier ma visibilité aux utilisateurs non connectés
    * Je peux me rendre visible
    * Je peux me rendre invisible (valeur par défaut)
- Je peux modifier mon adresse email
    * Avec confirmation sur email de récupération
- Je peux supprimer mon compte
    * Cela supprime toutes les informations liées au compte
- Je peux ajouter un email de récupération
- Je peux modifier mes informations de compte:
    * Pseudo
    * Email*
    * Mot de passe*
    * Capacitaire (Titulaire du Certificat de Capacité)
    * N° Capacitaire (si Capacitaire)
    * CDC (N° Certificat De Capacité)
    * AOE (N° Autorisation d'Ouverture d'Etablissement)
    * DD (N° Déclaration de détention)
    * Statut (Particulier ou professionnel)
    * Information Pro (si statut pro)*
      * SIRET*
        * Vérification via SIRENE Api
      * Raison Sociale*
    * Ville
    * Code Postal
    * Pays
    * Nom du Vétérinaire (clinique et/ou docteur)
    * Email du Vétérinaire
- Je peux avoir mon avatar
    * Ajouter (images prédéfinies)
    * Modifier (images prédéfinies)
    * Supprimer
    * Par défaut: image par défaut
- Je peux sélectionner les préférences alimentaire de mes animaux
    * Via une liste prédéfinie de types par défaut
    * En ajoutant des types de nourritures supplémentaires si besoin
- Je peux ajouter mes documents d'éleveur (documents légaux, CDC, AOE, etc)
- Je peux retier mes documents d'éleveur (idem)

### 3. Elevage

- En tant qu'éleveur, je peux
    * Créer un ou plusieurs élevages
      * Nom*
      * Description
    * Modifier un élevage
      * Nom*
      * Description
    * Supprimer un élevage
      * Seulement si aucun animal / aucun instalaltion n'est lié(e)
- En tant qu'éleveur, je peux
    * Ajouter un ou plusieurs animaux à un élevage (table différente, relation)
- En tant qu'éleveur, je peux (feature possible)
    * Sélectionner le type d'élevage que l'on souhaite créer*
      * par Animaux (table différente, relation)
      * par Installations 
    * Ajouter une ou plusieurs installations (si type = installations) (table différente, relation)
    * Retier une ou plusieurs installations (si type = installations) (table différente, relation)
  
### 4.Installation

- Informations d'installations: 
    * Identifiant appli (automatique)
    * Nom*
    * Description (matériaux de l'installation, informations complémentaires, etc)
    * Images (Photos) (table différente, relation)
    * Animaux (table différente, relation)
    * Type*
      * Terrarium
      * Aquaterrarium
      * Aquarium
      * Pièce
      * Enclos
      * Cage
      * Incubateur
    * Conditionnement*
      * Quarantaine
      * Nurserie
      * Standard
    * Environnement*
      * Stérile
      * Artificiel
      * Mixte
      * Naturel
    * Taille*
      * ***L*** x ***l*** x ***h***
      * Unité
        * Adaptative aux valeurs rentrées
          * cm par défaut
          * m si valeurs > 200
    * Volume
      * calcul automatique via la Taille
      * m³ par défaut
      * m² seulement si type = enclos
    * Type de chauffage* (choix multiple)
      * Lampe
      * Tapis
      * Câble
      * Aucun (naturel)
    * Puissance chauffage (totale)*
      * ***valeur totale*** W
    * Températures(°C)*
      * Jour
        * Point chaud
        * Point froid
      * Nuit
        * Point chaud
        * Point Froid
    * Hygrométrie (%)*
      * Jour
      * Nuit
    * Type d'éclairage* (choix multiple)
      * Naturel
      * Lampe classique
      * LED
      * Lampe UV
      * Néon classique
      * Néon UV
    * Puissance éclairage*
      * ***valeur*** UV
      * ***valeur*** Lumens
    * Historique
      * Evènements (table différente, relation)
        * nom
        * description
        * date (automatique à la création de l'événement)
- En tant qu'éleveur je peux
    * Créer une ou plusieurs installations
    * Modifier mon installation
      * Informations globales de l'installation
      * Ajouter un événement à l'historique
    * Supprimer mon installation
      * Seulement si elle n'a pas d'animaux liés

### 5. Animal

- Informations de l'animal
    * Identifiant appli (automatique)
    * Nom scientifique* (genre, espèce et sous-espèce (si il y a)) (italique)
    * Nom vernaculaire (nom commun)
    * Nom de l'animal
    * Date de naissance* (date ou inconnue)
    * Âge (automatique via date de naissance, **/** si inconnue)
    * Sexe* (Mâle, Femelle, Indéterminé) (♂, ♀)
    * Taille
      * cm par défaut
      * m si > 100
    * Poids
      * g par défaut
      * kg si > 1000
    * Statut CITES (I, II, III, aucun) (convention de washington)
    * Statut UE (A, B, C, D, aucun)
    * Statut FR (1, 2, 3, aucun)
    * CDC* (oui, non, non renseigné)
    * Identification* (N° CITES, puce, ifap, aucun)
    * N° d'identification* (CITES, puce/transpondeur, Ifap, etc)
    * Provenance* (Eleveur, Animalerie, Grossiste)
    * Nom provenance* (Nom de l'éleveur, de l'animalerie ou du grossiste)
    * Origine* (Né en captivité (NC), Capturé en milieu naturel(WC),Farming, Inconnue )
    * Répartition géographique* (Origine géographique naturelle de l'animal - le ou les Pays)
    * Photos
    * Notes (Toutes autres informations à donner concernant l'animal)
- En tant qu'éleveur, je peux
    * Créer un animal
      * Son carnet de santé se crée en même temps
      * Son suivi de nourrissage se crée en même temps
    * Modifier un animal
    * Supprimer un animal
    * Exporter la fiche de mon animal au format pdf
- En tant qu'éleveur, je dois
    * Associer mon animal à une installation
      * existante
      * en créer une nouvelle pour lui
- En tant qu'éleveur, je peux 
    * Ajouter un animal à un élevage (de type animal)
    * Retirer un animal d'un élevage (de type animal)
    * Transférer un animal d'une installation à une autre (un animal doit être obligatoirement lié à une installation)
- Fichiers (papiers légaux: certificat de cession, certificat de naissance, etc)

### 6. Suivi de nourrissage
- Informations de nourrissage
    * Type* (table) (liste des types de nourritures via les choix de l'éleveur)
    * Date*
    * Prise* (Oui / Non)
    * Quantité*
    * Unité* (de quantité)
      * g
      * kg
    * Description* (toutes autres informations nécessaires à préciser)
- Il se crée automatiquement lors de la création d'un animal
- En tant qu'éleveur, je peux
    * Ajouter un événement de nourrissage
    * Modifier un événement de nourrissage
- En tant qu'éleveur, je ne peux pas
    * Supprimer un événement de nourrissage

### 7. Carnet de santé
- Informations du carnet
    * Date*
    * Titre
    * Type* (Mue, Ponte/Mise-bas, Traitement, Rdv Véto, Santé, Comportement, Autre)
    * Détails (informations détaillées sur l'événement de santé)
    * Liens en fonction du type (animal monitoring)
      * Rdv Véto
        * Date*
        * Raison*
        * Bilan
      * Traitement
        * Date*
        * Posologie* (quantité / fréquence)
        * Médicament*
        * Détails
    * Fichiers médicaux (ordonnance, rdv véto, etc) et Images d'événements
- Le carnet de santé se crée en même temps
- En tant qu'éleveur, je peux
  * Ajouter un événement de santé
  * Modifier un événement de santé 
  * Ajouter une image à un événement de santé
  * Ajouter un fichier au carnet de santé
  * Voir le graphique d'évolution de l'Âge/Taille/Poids de l'animal dans le carnet de santé

### 8. Export PDF et envoi des informations importantes (carnet de santé)

-  En tant qu'éleveur, je peux
    * Exporter les informations du carnet de santé de mon animal (en PDF)
    * Envoyer les informations directement par email à mon vétérinaire
      * seulement si l'email du vétérinaire est renseignée

### 9. Utilisation de QRcode pour le suivi global

- Un QRcode unique se génère automatiquement à la création d'une installation
    * En utilisant l'identifiant appli + nom (si renseigné) + id (db)
- En tant qu'éleveur, je peux
    * Enregistrer le QRcode au format pdf (pour impression)
      * en petite taille
    * Scanner le QRcode imprimé pour avoir toutes les informations de mon installation ainsi que les animaux qui y vivent.
    * Scanner le QRcode de l'installation vers laquelle on souhaite transférer un animal depuis une autre.

### 10. Dashboard

- En tant qu'éleveur, je peux
    * Accéder à la liste de mes animaux
      * Voir tous mes animaux
      * Trier mes animaux
      * Sélectionner un ou plusieurs animaux
        * Transférer la sélection
        * Supprimer la sélection
    * Accéder à la liste de mes installations
      * Voir toutes mes installations
      * Trier mes installations
      * Sélectionner une ou plusieurs installations
        * Supprimer la sélection
          * Seulement si aucun animal lié
    * Accéder à la liste de mes élevages
      * Voir mes élevages
      * Sélection un ou plusieurs élevages
        * Supprimer la sélection
    * Accéder à l'ajout d'un événement de nourrissage (pour animal ou pour une installation)
    * Accéder à l'ajout d'un événement d'une installation (maintenance, etc)
    * Accéder à l'ajout d'un événement de santé (soins, mesures et autres)
    * Voir l'historique des 5 derniers événements (par date décroissante) pour
      * Nourrissage
      * Carnet de santé (rdv véto, traitements, mesures)
      * Divers (entrées, sorties, nouvelle installations, transferts, etc)

## VII. Sprints

## VIII. Charte graphique / IHM

### Logotype
*Logos réalisés par **[Angélique Salomon](http://angelique-salomon.fr/) - Graphiste***

### Couleurs
- logo :
    * `#477b6f` - rgb(71,123,111)
    * `#c8d2c4` - rgb(200,210, 196)

### Typographie
Le choix de la typographie a aussi été fait avec Angélique, et ce sera l'[ASAP](https://fonts.google.com/specimen/Asap?sidebar.open=true&selection.family=Asap)

## IX. Glossaire

- CDC : Certificat De Capacité (Législation française de détention)