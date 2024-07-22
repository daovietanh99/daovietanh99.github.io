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
To configure Django Database, we have to edit the `settings.py` file. By default, Django pre-defines the config and connection to the Sqlite DB. Sqlite, itselfs, does not have a backend server running in dedicated environment; it's just a file and all the logic and interfaces are built-in library. So, you can check that the URI is just a location to the sqlite's db file called `db.sqlite3`.

```python

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': BASE_DIR / 'db.sqlite3',
    }
}

```

#### Sqlite3
#### Postgres
### Define a model
### Not null, not blank
### Relation field
### Unique field method
### File field
### Abstract model
