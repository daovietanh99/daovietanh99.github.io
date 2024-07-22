---
date: 17-07-2024
coverimg: /static/img/cover.jpg
permalink: /posts/render/django-models-handle-django-application-models
---

# Django Models: Handle Django Rest Framework application models

![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![Django](https://img.shields.io/badge/django-%23092E20.svg?style=for-the-badge&logo=django&logoColor=white)
![DjangoREST](https://img.shields.io/badge/DJANGO-REST-ff1709?style=for-the-badge&logo=django&logoColor=white&color=ff1709&labelColor=gray)

In previous post, we have just created and runned a Django project and application. So, on this post and other later posts, we will go deeper on how to develop a completed application. First and foremost, I want to talk about database, as you know, database (relation database) is very important for most application. It contains data of users, clients, applications and so on. Some of the popular databases we can list here: Postgres, Mysql. There are many ways to connect an application to a database, and in Django we have ORM, stands for Object Relational Mapping. ORM is a technique that lets you query and manipulate data from a database using an object-oriented paradigm. Instead of working with tables, we now work with objects!

### Connect to a database

#### Sqlite3
To configure Django Database, we have to edit the `settings.py` file. By default, Django pre-defines the config and connection to the Sqlite DB. Sqlite, itselfs, does not have a backend server running in dedicated environment; it's just a file and all the logic and interfaces are built-in library. So, you can check that the URI is just a location to the sqlite's db file called `db.sqlite3`.

```python

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': BASE_DIR / 'db.sqlite3',
    }
}

```

#### PostgreSQL
 We need to install the PostgreSQL database adapter to communicate to the database with Python to install it run the following command in the shell.
```shell
pip install psycopg2
```

We also need to update these settings to integrate our PostgreSQL with the project.
```python

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql_psycopg2',
        'NAME': 'mydb',
        'USER': 'myuser',
        'PASSWORD': 'mypass',
        'HOST': 'localhost',
        'PORT': '5432',
    }
}

```
After configuring the `setting.py` we go to root project and run the server to test the connection. If our project successfully connected without any errors, the connection is success and vice versa.

### Migrate the database
The database migration process ensures the tables of database keep track with all Django project logic and models. To run your first migrate process, type the bellow command to generate migration file.

```shell
python3 manage.py makemigrations
```

The migration files will appear inside `migrates` folder of each application, their name start with a four-characters number (0001, 0002, ...). The migration files reflect the process of creating or updating tables for keeping track with current model definitions. To apply the migrations, we run the command

```shell
python3 manage.py migrate
```

Your output will look something like that

![migrate output](/static/img/django-models-handle-django-application-models/django-models-handle-django-application-models-1.png)

Now, you can check the database and make sure all tables look like what you have created.

### Define a model


### Not null, not blank
### Relation field
### Unique field method
### File field
### Abstract model
