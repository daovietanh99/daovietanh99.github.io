---
date: 16-07-2024
coverimg: /static/img/cover.jpg
permalink: /posts/render/create-your-first-django-project
---

# Create your first Django project  

	![Django](https://img.shields.io/badge/django-%23092E20.svg?style=for-the-badge&logo=django&logoColor=white)
 ![DjangoREST](https://img.shields.io/badge/DJANGO-REST-ff1709?style=for-the-badge&logo=django&logoColor=white&color=ff1709&labelColor=gray)

In this post, I will demonstrate a simple Django Web App. My tutorial focuses on the initial steps you’ll need to take to start a new web application. To start a django project, we simply use the bellow command:

```shell
python -m django-admin startproject your_project_name
```

Once you run this command, a Django project with following structure will be created inside your your_project_name folder. Let's pay attention on some project components. Firstly, we have `manage.py` file, 


We then can run the server by applying the following command:

```shell
python manage.py runserver host:port
```

Where, host and port are 
