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
Connection à la base de données

```python
conn = psycopg2.connect(database = "postgresql",  # nom par defaut
                        user = "postgresql", # nom par defaut
                        host= 'localhost',
                        password = "password,
                        port = 5432) # port par defaut
```






Annexes :


- Ressources SQL sur le site officiel de PostgreSQL :
https://www.postgresql.org/about/

-Guide du débutant sur PostgreSQL : 
https://www.datacamp.com/tutorial/beginners-introduction-postgresql
