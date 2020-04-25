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
 |    |-- myproject/
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

for creating a custom app component
```
python manage.py startapp app_name
```

