## Get started



### Installation de MongoDB

Téléchargez et installez MongoDB à partir du [site officiel de MongoDB](https://www.mongodb.com/try/download/community).

### Démarrage du Serveur MongoDB

1. Ouvrez un terminal.

2. Démarrez le serveur MongoDB avec la commande suivante :
   ```bash
   mongod
   ```

### Connexion à MongoDB

1. Ouvrez un nouveau terminal (laissez le serveur MongoDB s'exécuter dans le terminal précédent).

2. Connectez-vous à MongoDB avec la commande suivante :
   ```bash
   mongo
   ```

### Création d'une Base de Données et d'une Collection

1. Dans le shell MongoDB, créez une nouvelle base de données :
   ```bash
   use ma_base_de_donnees
   ```

2. Créez une collection (similaire à une table dans les bases de données relationnelles) :
   ```bash
   db.createCollection("ma_collection")
   ```

### Insertion de Données

1. Insérez des données dans la collection :
   ```bash
   db.ma_collection.insert({ nom: "John Doe", age: 30, ville: "Paris" })
   ```

### Recherche de Données

1. Recherchez toutes les entrées dans la collection :
   ```bash
   db.ma_collection.find()
   ```

2. Recherchez des entrées spécifiques :
   ```bash
   db.ma_collection.find({ nom: "John Doe" })
   ```

### Suppression de Données

1. Supprimez une entrée spécifique :
   ```bash
   db.ma_collection.remove({ nom: "John Doe" })
   ```

2. Supprimez toutes les entrées dans la collection :
   ```bash
   db.ma_collection.remove({})
   ```

### Déconnexion de MongoDB

Dans le shell MongoDB, déconnectez-vous en utilisant la commande suivante :
   ```bash
   exit
   ```

## Configuration de Sécurité et de Performance MongoDB

### Paramètres de Sécurité

### Activer l'Authentification

1. **Activez l'authentification dans MongoDB :**
   - Éditez le fichier de configuration (habituellement `mongod.conf`) et ajoutez les lignes suivantes :
     ```
     security:
       authorization: enabled
     ```

2. **Créez un utilisateur administrateur :**
   - Connectez-vous à MongoDB et créez un utilisateur administrateur.
     ```bash
     use admin
     db.createUser({ user: "admin", pwd: "mot_de_passe", roles: ["userAdminAnyDatabase"] })
     ```

3. **Redémarrez MongoDB avec l'authentification :**
   - Redémarrez le serveur MongoDB avec l'authentification activée.

### Configuration des IP Autorisées

1. **Autorisez uniquement certaines IP à se connecter :**
   - Éditez le fichier de configuration et ajoutez les lignes suivantes :
     ```
     net:
       bindIp: 127.0.0.1,IP_autorisee
     ```

2. **Redémarrez MongoDB :**
   - Redémarrez le serveur MongoDB pour appliquer les changements.

### Chiffrement des Connexions avec SSL/TLS

1. **Générez des certificats SSL/TLS :**
   - Générez des certificats SSL/TLS pour sécuriser les connexions.

2. **Configuration de MongoDB pour utiliser SSL/TLS :**
   - Éditez le fichier de configuration et ajoutez les lignes suivantes :
     ```
     net:
       ssl:
         mode: requireSSL
         PEMKeyFile: chemin/vers/clé.pem
         PEMCertificateFile: chemin/vers/certificat.pem
     ```
### Paramètres de Performance

#### 1. Ajustez les paramètres de la mémoire :

   - Ouvrez le fichier de configuration (`mongod.conf`) et ajoutez ou modifiez la ligne suivante :
     ```
     storage:
       wiredTiger:
         engineConfig:
           cacheSizeGB: <valeur_en_gigaoctets>
     ```
   - Remplacez `<valeur_en_gigaoctets>` par la taille souhaitée pour le cache, par exemple, `4` pour 4 gigaoctets.

#### 2. Configurez les indexes judicieusement :

   - Identifiez les champs fréquemment utilisés dans les requêtes et créez des indexes pour ces champs.
     ```javascript
     db.maCollection.createIndex({ champ1: 1, champ2: -1 })
     ```
   - Assurez-vous de ne pas créer trop d'indexes, car cela peut affecter les performances d'écriture.

#### 3. Surveillez l'utilisation des ressources :

   - Utilisez MongoDB Profiler pour surveiller les requêtes lentes ou coûteuses.
     ```javascript
     db.setProfilingLevel(1, { slowms: 100 })
     ```
   - Utilisez MMS (MongoDB Monitoring Service) ou d'autres outils de surveillance pour suivre les métriques de performance.

### Sauvegardes Régulières

#### 1. Planifiez des sauvegardes régulières :

   - Utilisez l'outil `mongodump` pour effectuer des sauvegardes régulières de vos bases de données.
     ```bash
     mongodump --out /chemin/vers/dossier/sauvegarde
     ```

#### 2. Testez les Procédures de Restauration :

   - Assurez-vous que vous pouvez restaurer les données à partir des sauvegardes.
     ```bash
     mongorestore /chemin/vers/dossier/sauvegarde
     ```

### Mises à Jour Régulières

#### 1. Mettez à jour MongoDB régulièrement :

   - Vérifiez les dernières versions stables de MongoDB et effectuez les mises à jour nécessaires.
     ```bash
     # Exemple pour Ubuntu
     sudo apt-get update
     sudo apt-get upgrade mongodb-org
     ```

### Audit des Activités

#### 1. Activez l'audit des activités :

   - Modifiez le fichier de configuration pour activer l'audit des opérations.
     ```
     auditLog:
       destination: file
       path: /chemin/vers/fichier/logs/auditLog.json
     ```

#### 2. Surveillez les Logs d'Audit :

   - Consultez régulièrement les logs d'audit pour détecter toute activité suspecte.

### Tests de Sécurité

#### 1. Effectuez des tests de sécurité :

   - Utilisez des outils de test de sécurité, tels que MongoDB Security Checklist, pour identifier les vulnérabilités potentielles.
     ```bash
     mongosec
     ```

