# Configure_PostgreSQL_for_Python
Créer, se connecter et gérer des bases de données PostgreSQL à l’aide du package psycopg2 de Python.

Installation de PostgreSQL sur son poste

Télécharger et installer PostgreSQL sur son poste :

https://www.postgresql.org/download/

Installation de la librairie psycopg2

```shell
pip install psycopg2
```

Installation de la librairie psycopg2-binary

```shell
pip install psycopg2-binary
```

Appel de la librairie psycopg2 dans Python

```python
import psycopg2
```
Connection à la base de données ### PYTHON <==> POSTGRESQL ###

Pour permettre Python d'interagir avec PostgreSQL, nous devons créer une connection entre eux, et cela se fait avec la fonction psycopg2 ".connect()"

```python
conn = psycopg2.connect(database = "postgresql",  # nom par defaut
                        user = "postgresql", # nom par defaut
                        host= 'localhost',
                        password = "password,
                        port = 5432) # port par defaut
```

Les paramètres de connexion de base requis sont :

- database. Nom de la base de données.
- user. Nom d'utilisateur requis pour l'authentification.
- host (hôte). Adresse du serveur de base de données (dans notre cas, la base de données est hébergée localement, mais il pourrait s'agir d'une adresse IP).
- password. Mot de passe utilisé pour l'authentification.
- port. Numéro de port de connexion (par défaut : 5432 s'il n'est pas fourni).


Créer une table dans PostGreSQL

Nous allons créer une table du projet Yellow taxis trips, avec le schémla suivant :

![""](schema_table_taxis_zone.jpg)

Avant de créer la table, il est important d'expliquer le fonctionnement de l'instance de connexion que vous venez de créer. 
En résumé, la connexion encapsule une session de base de données et vous permet d'exécuter des commandes et des requêtes SQL, 
telles que SELECT, INSERT, CREATE, UPDATE ou DELETE, à l'aide de la méthode cursor(), et de rendre les modifications persistantes grâce à la méthode commit().

Une fois l'instance du curseur créée, vous pouvez envoyer des commandes à la base de données via la méthode execute() et récupérer des données d'une table via fetchone(), fetchmany() ou fetchall().
Enfin, il est important de fermer le curseur et la connexion à la base de données une fois vos opérations terminées. Sinon, ils continueront de détenir des ressources côté serveur. 
Pour ce faire, vous pouvez utiliser la méthode close().


Pour résumer :
- méthode :
  * .connect() ==> établir une connexion entre Python et le serveur de base de données
  * .cursor() ==> exécuter des requêtes SQL (```SELECT```, ```INSERT```, ```UPDATE```, ```DELETE```, etc.), & récupérer les résultats de ces requêtes.
      -    Il agit comme un intermédiaire entre Python et la base de données.
      -    Il gère l’envoi et la réception des commandes SQL.
        
**Exemple d’utilisation**
```python
# Création d'un curseur
cursor = conn.cursor()

# Exécution d'une requête SQL
cursor.execute("SELECT * FROM utilisateurs")

# Récupération des résultats
resultats = cursor.fetchall()

# Affichage des résultats
for ligne in resultats:
    print(ligne)

# Fermeture du curseur
cursor.close()
```

  * .commit() ==> rendre les modifications persistantes
  * .execute() ==> envoyer des commandes à la base de donnée
  * .fetchone() ==> récupérer des données d'une table >>> une seule ligne
  * .fetchmany() ==> récupérer des données d'une table >>> un certain nombre de lignes défini par ```size```
  * .fetchall() ==> récupérer des données d'une table >>> toutes les lignes restantes du résultat de la requête et les retourne sous forme d'une liste.
  * .close() ==> fermer le curseur et la connexion à la base de données une fois vos opérations terminées
 
```pyhon
# Open a cursor to perform database operations
cur = conn.cursor()
# Execute a command: create taxis_zone table
cur.execute("""CREATE TABLE taxi_zone(
            LocationID INT,
            Borough VARCHAR (250),
            Zone VARCHAR (250),
            service_zone VARCHAR (250));
            """)
# Make the changes to the database persistent
conn.commit()
# Close cursor and communication with the database
cur.close()
conn.close()
```


Exécution de requêtes PostgreSQL basiques en Python






































**Résumé des étapes complètes**

| Étape       | Action                      | Code associé                                 |
|-------------|-----------------------------|----------------------------------------------|
| 1. Connexion | Se connecter à la base de données | `conn = psycopg2.connect(...)`              |
| 2. Création d'un curseur | Permet d'exécuter des requêtes | `cursor = conn.cursor()`                     |
| 3. Exécution de requêtes | Envoyer une commande SQL      | `cursor.execute("SELECT * FROM table")`       |
| 4. Récupération des données | Obtenir les résultats       | `cursor.fetchall()`                           |
| 5. Fermeture | Fermer le curseur et la connexion | `cursor.close(), conn.close()`               |














































Annexes :
- Documentation psycopg2 :
https://www.psycopg.org/docs/install.html#install-from-source

- Ressources SQL sur le site officiel de PostgreSQL :
https://www.postgresql.org/about/

- Guide du débutant sur PostgreSQL : 
https://www.datacamp.com/tutorial/beginners-introduction-postgresql
