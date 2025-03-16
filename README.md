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






Annexes :
- Documentation psycopg2 :
https://www.psycopg.org/docs/install.html#install-from-source

- Ressources SQL sur le site officiel de PostgreSQL :
https://www.postgresql.org/about/

-Guide du débutant sur PostgreSQL : 
https://www.datacamp.com/tutorial/beginners-introduction-postgresql
