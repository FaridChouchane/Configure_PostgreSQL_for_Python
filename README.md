# Configure_PostgreSQL_for_Python
configuration de PostgreSQL sous Python


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