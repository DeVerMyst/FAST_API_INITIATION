#### Conception du projet
* création d'un dossier de travail
* création des fichiers
  * .venv (pour l'environnement virtuel)
  * .env (les variables d'environnement)
  * la procédure d'installation:
    * README.md 
    * requirements.txt 
  * .gitignore (pour le versionnage)
* séparation de l'architecture
  * dossiers:
    * APP : contient toute l'application
    * backend : contient la logique data
    * API_IA : contient la logique IA
  * architecture en couche
    * séparation des modules
    * séparation des modèles
    * séparation des données 

#### logique / étapes
**Application**
* importation des bibliothèques
* chargement des variables d'environnement
* créations des pages:
  * accueil:
    * bouton de ping de l'API type `hello world`
    * transaction get avec la route `'/'`
  * insérer:
    * formulaire pour l'insertion des données
    * transaction post avec la route `'/insert'`
    * gestion des exceptions

**API backend**
* importation des bibliothèques
* chargement des variables d'environnement
* création de l'API
* définition des modèles pydantic
* initialisation de la base de données
  * création si elle n'existe pas
* définition des routes
  * route principale - get 
    * hello world
  * route insert - post 
    * vérifie les données, voir choisir un index
    * conversion en df
    * ecriture en base de données
    * retourne une info sous forme de dictionnaire
  * route read - get
    * lecture de la base de données complète
    * retourne un df
  * route read/id - get 
    * **lecture de la base de données complète**
    * filtre un id dans le df
    * retourne un df
  * logique pour lancer l'API

#### Architecture
```
mon_projet/
├── backend
│   ├── modules
│       ├── db_tools.py
│   │   └── df_tools.py
│   ├── data
│   │   └── quotes_db.csv
│   └── main.py
├── frontend
│   ├── app.py
│   └── pages
│       ├── 0_insérer.py
│       ├── 1_Afficher.py
│       └── 2_Rechercher.py
├── tests
│   ├── test_backend_api.py
│   └── test_backend_orm.py
├── README.md
├── pytest.ini
├── .env
├── .venv
└── .gitignore
```