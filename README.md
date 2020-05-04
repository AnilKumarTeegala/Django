# Django
[![Python Version](https://img.shields.io/badge/python-3.x-brightgreen.svg)](https://python.org)
[![Django Version](https://img.shields.io/badge/django-3.0.3-brightgreen.svg)](https://djangoproject.com)

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

![Webserver_Home](../img/webserver.png)



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

**`Note:`** After creating app we need to append our `app` name to **`INSTALLED_APPS`** list in **`setting.py`**

## Your First App Component

By completing the above steps I have created an app called **`Products`**

I'm using this app for creating products. So for storing the data of the product into the backend / Database we need too create it so for adding it we need to create it in `models.py` of `products` app. I'm considering the 4 parameters they are
1. Title
2. Description
3. Price
4. Summary
so for adding it I've created a class in `manage.py` like shown below and save it

```python
from django.db import models

# Create your models here.
class Product(models.Model):
	title 		= models.TextField()
	description = models.TextField()
	price       = models.TextField()
	Summary     = models.TextField(default = 'This is cool!') # default is th arg which will be stored if no data is entered
 ```
After add above we need to make migrate our database to save the changes to it
```
python manage.py makemigrations
```
```
python manage.py migrate
```
**`Note:`** Whenever we made change to the manage.py --> changes to DB occur to save it we need to migrate 

finally after making change if we login to http://127.0.0.1:8000/admin we need to see the Products and by clicking it we can observe list of product avaliable as shown like below

![firstProduct](../img/firstProduct.png)


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
```python
from app.models import app
```
so for listing the all elements in the database we have execute
```python
app.objects.all()
```
if we want to create new elements to the db
```python
app.object.create(arg1 = data, arg2 = data, ..... argn = data)
```


## Day4 28 April 2020

## Change a Model

So Yesterday I have created Products app and add 4 fields in the `models.py`

so if we observe we see that some `TextFields` they are to type of Model fields we can find out them at [Model field ](https://docs.djangoproject.com/en/3.0/ref/models/fields/) so by going to documentation I have choosen the integer type to the prices and updated the arguments to the fields as shown below
```python
from django.db import models

# Create your models here.
class Product(models.Model):
	title 		= models.CharField(max_length = 120)
	description = models.TextField(blank = True, null = True)
	price       = models.DecimalField(decimal_places = 2, max_digits = 1000)
	Summary     = models.TextField(default = 'This is cool!')
	features	= models.BooleanField(default = True, null = False)
```
after updating the field we can them by loging into http://127.0.0.1:8000/admin/ and going to Products as shown below

![updateProduct](../img/updateProduct.png)

## Default Homepage to Custom Homepage
For Pages I'll be creating an app called **`pages`**

To change the Home page to the custom home page we need to add the required html content by creating a function in the `views.py` in the created app and we need to update `url.py` in the project by importing and adding the path

example:
Updating `views.py`
```python
from django.http import HttpResponse

def home_view(*args, **kwargs):
	return HttpResponse("<h1>Hello World Django</h1>")
```
and updating `url.py` like below
```python
from django.contrib import admin
from django.urls import path

from pages.views import home_view

urlpatterns = [path('home/', home_view, name='home')]
 ```
thats it if we visit `http://127.0.0.1:8000/home/` we can see the `Hello World Django` in H1 font

## URL Routing and Requests
Like above we can add as many pages as we need by adding HTTP responses to the `views.py` and urls in the `urls.py` as shown below
**`views.py`**
```python
from django.http import HttpResponse
from django.shortcuts import render

def home_view(*args, **kwargs):
	return HttpResponse("<h1>Hello World Django</h1>")

def contact_view(*args, **kwargs):
	return HttpResponse("<h1>Contact Page</h1>")

def about_view(*args, **kwargs):
	return HttpResponse("<h1>About Page</h1>")

def social_view(*args, **kwargs):
	return HttpResponse("<h1>Social Page</h1>")
```

**`urls.py`**
```python
from django.contrib import admin
from django.urls import path

from pages.views import home_view, contact_view, social_view, about_view

urlpatterns = [
	path('', home_view, name='home'),
	path('about/', about_view, name = 'about'),
	path('home/', home_view, name='home'),
	path('social/', social_view, name = 'social'),
	path('contact/', contact_view, name='home'),
path('admin/', admin.site.urls),
]
```

## Django Templates
