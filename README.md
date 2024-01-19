# mongodb get started


### Étape 1: Installation de MongoDB

Téléchargez et installez MongoDB à partir du [site officiel de MongoDB](https://www.mongodb.com/try/download/community).

### Étape 2: Démarrage du Serveur MongoDB

1. Ouvrez un terminal.

2. Démarrez le serveur MongoDB avec la commande suivante :
   ```bash
   mongod
   ```

### Étape 3: Connexion à MongoDB

1. Ouvrez un nouveau terminal (laissez le serveur MongoDB s'exécuter dans le terminal précédent).

2. Connectez-vous à MongoDB avec la commande suivante :
   ```bash
   mongo
   ```

### Étape 4: Création d'une Base de Données et d'une Collection

1. Dans le shell MongoDB, créez une nouvelle base de données :
   ```bash
   use ma_base_de_donnees
   ```

2. Créez une collection (similaire à une table dans les bases de données relationnelles) :
   ```bash
   db.createCollection("ma_collection")
   ```

### Étape 5: Insertion de Données

1. Insérez des données dans la collection :
   ```bash
   db.ma_collection.insert({ nom: "John Doe", age: 30, ville: "Paris" })
   ```

### Étape 6: Recherche de Données

1. Recherchez toutes les entrées dans la collection :
   ```bash
   db.ma_collection.find()
   ```

2. Recherchez des entrées spécifiques :
   ```bash
   db.ma_collection.find({ nom: "John Doe" })
   ```

### Étape 7: Suppression de Données

1. Supprimez une entrée spécifique :
   ```bash
   db.ma_collection.remove({ nom: "John Doe" })
   ```

2. Supprimez toutes les entrées dans la collection :
   ```bash
   db.ma_collection.remove({})
   ```

### Étape 8: Déconnexion de MongoDB

Dans le shell MongoDB, déconnectez-vous en utilisant la commande suivante :
   ```bash
   exit
   ```

Ceci conclut le tutoriel de démarrage rapide pour MongoDB. Ces étapes de base vous aideront à créer une base de données, à insérer des données, à effectuer des recherches et à supprimer des données dans MongoDB. Vous pouvez également explorer davantage les fonctionnalités avancées de MongoDB en consultant la documentation officielle.

