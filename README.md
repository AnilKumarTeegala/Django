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

## Starting a New Project
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
 
 
