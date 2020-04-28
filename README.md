# Django
[![Python Version](https://img.shields.io/badge/python-3.x-brightgreen.svg)](https://python.org)
[![Django Version](https://img.shields.io/badge/django-2.1.5-brightgreen.svg)](https://djangoproject.com)

This repo containg the learning content of Django



# Day-1: 24 April 2020

While working on Django it is better to create a virtual environment to run project files.

## Steps for creating virtualenv on window 10

### 1. Install virtual environment
```
pip install virtualenv
```

### 2. Download and install pip
**`Note:`** If pip command is not found then follow the below step else continue tonext step
```
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
```
```
python3 get-pip.py
```


### 3. Start virtualenv
In windows command prompt, navigate to your project location: 
```
mkdir Django
cd Django
```
Once inside the project folder run: 
```
virtualenv env_name
```
### 4. Activate virtualenv

To activate virtualenv on Windows, and activate the script is in the Scripts folder:

```
env_name\Scripts\activate.bat
```


## Installing Django 

Now we have the venv activated, run the following command to install Django:
```
pip install django
```

Thats it all setup now

## Creating a Blank Django Project
To start a new Django project, run the command below:
```
django-admin startproject project1
```

The command-line utility **django-admin** is automatically installed with Django.

After we run the command above, it will generate the base folder structure for a **Django project**.

Right now, our **Django** directory looks like this:

```
Django/                  <-- higher level folder
 |-- myproject/             <-- django project folder
 |    |-- project1/
 |    |    |-- __init__.py
 |    |    |-- settings.py
 |    |    |-- urls.py
 |    |    |-- wsgi.py
 |    +-- manage.py
 +-- venv/                  <-- virtual environment folder
 ```
### Working on Project

Django comes with a simple web server installed. It’s very convenient during the development, so we don’t have to install anything else to run the project locally. We can test it by executing the command:
```
python manage.py runserver
```
For now, you can ignore the migration errors; we will get to that later.

Now open the following URL in a Web browser: http://127.0.0.1:8000 and you should see the following page:

![Webserver_Home](img/webserver.png)






# Day2 25 April 2020

## Built-In Components

To accessing the admin login page visit

http://127.0.0.1:8000/admin/login/?next=/admin/


For creating the login credentails we need to migrate defalult Admin db schema so for doing it execute

```
python manage.py migrate
```

For creating a user with admin permissions

```
python manage.py createsuperuser
```
and set your username, email(not compulsory) and passsword


## My First App Component

for creating a `custom-app` component
```
python manage.py startapp app_name
```
after creating we can see the directory structure as shown delow

```
Django/
 |-- myproject/             <-- django project folder
 |    |-- app_name/                <-- our new django app!
 |    |    |-- migrations/
 |    |    |    +-- __init__.py
 |    |    |-- __init__.py
 |    |    |-- admin.py
 |    |    |-- apps.py
 |    |    |-- models.py
 |    |    |-- tests.py
 |    |    +-- views.py
 |    |-- project1/
 |    |    |-- __init__.py
 |    |    |-- settings.py
 |    |    |-- urls.py
 |    |    |-- wsgi.py
 |    +-- manage.py
 +-- venv/                  <-- virtual environment folder
```

**`Note:`** After creating app we need to add the app name at `INSTALLED_APPS` list in `setting.py`

# Day3 27 April 2020

## Create `app` Objects in the Python Shell

To Execute the commands in the cell we have to execute

```
python manage.py shell
```
python shell will be open like shown below

```
Python 3.8.2 (tags/v3.8.2:7b3ab59, Feb 25 2020, 23:03:10) [MSC v.1916 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
(InteractiveConsole)
```

For writing the data in to an app using shell we hve to import it
```
from app.models import app
```
so for listing the all elements in the database we have execute
```
app.objects.all()
```
if we want to create new elements to the db
```
app.object.create(arg1 = data, arg2 = data, ..... argn = data)
```
## Day4 28 April 2020 
## Change a Model
## Default Homepage to Custom Homepage
## URL Routing and Requests
## (1:10:23) 14 - Django Templates
