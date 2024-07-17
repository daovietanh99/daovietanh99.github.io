---
date: 16-07-2024
coverimg: /static/img/cover.jpg
permalink: /posts/render/create-your-first-django-project
---

# Django Tutorial: Create your first Django Rest Framework project  

![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![Django](https://img.shields.io/badge/django-%23092E20.svg?style=for-the-badge&logo=django&logoColor=white)
![DjangoREST](https://img.shields.io/badge/DJANGO-REST-ff1709?style=for-the-badge&logo=django&logoColor=white&color=ff1709&labelColor=gray)

In this post, I will demonstrate a simple Django Web App. My tutorial focuses on the initial steps you’ll need to take to start a new web application.

### Environment Preparation

Firstly, you have to setup virtual environment for your project, you can use either `virtualenv` or `conda` to create new python3.10 environment and make sure you have activated it. Then, you have to install `django`, `django-admin` and `djangorestframework` package to local. You may want to use `python3` command as well, in case you need to make sure that every packages are installed in the right place.

```shell
python3 -m pip install django django-admin djangorestframework
```

### Create Django project

To start a django project, we simply use the bellow command:

```shell
python3 -m django startproject your_project_name
```

Once you run this command, a Django project with following boilerplate structure will be created inside your your_project_name folder. Let's pay attention on some project components. Firstly, we have `manage.py` file, where we can run django command from here. Go deeper we have a folder which name is as the same as the project name. Inside, we have `settings.py` file, that stores the project configuration; `urls.py` file contains API endpoints and routers, and `asgi.py` and `wsgi.py` for running server engine.

```shell
tree your_project_name
your_project_name
├── manage.py
└── your_project_name
    ├── asgi.py
    ├── __init__.py
    ├── settings.py
    ├── urls.py
    └── wsgi.py
```

We then can run the server by applying the following command in the project's root folder:

```shell
python3 manage.py runserver host:port
```

Where, host and port are respectively the IP of host server and the port you want the application to run on. In my example, I use `0.0.0.0` for host IP and `8000` for port. Using `0.0.0.0` helps us exposing the application to outbound network. After running the Django project, we will get something like following.

![runserver output](/static/img/create-your-first-django-project/create-your-first-django-project-1.png)

You will still see some warning message in red color, I will talk about it later. Your project are now running, but it still can do nothing due to lack of database connecting, controller code, API, ... etc. In the next step, we will make an application for our Django project.

### Create Django application

Django project will have multiple applications, Django project itself is a root application, other applications themselves can be thought as sub-applications or sidecar applications. They can interact with one and others. We can easily create an application by using this command inside project root folder.

```shell
python3 manage.py startapp your_app_name
```

Now, Let's look at new application is created inside folder `your_app_name`

```shell
your_app_name
├── admin.py
├── apps.py
├── __init__.py
├── migrations
│   └── __init__.py
├── models.py
├── tests.py
└── views.py
```

We also have some boilerplate components, they are `admin.py`, `apps.py`, `migrations`, `models.py`, `tests.py` and `views.py`. We then only focus on some mainly use components on this tutorial like `apps.py`, `models.py`, `migrations` and `views.py`. For `apps.py`, it contains definement and configuration of the application. Next to `models.py` and `migrations`, they are themselves ORM components for connecting, modeling, migrating database. Finally, we have 'views.py', different from View element on MVC model, view in Django has the same functionality as Control element in MVC model. 

We now can run the project again and check the output.

In the next posts, I will go through all components and get into details to build a completed Django Rest Framework project. Thanks for watching. See you then !!!
