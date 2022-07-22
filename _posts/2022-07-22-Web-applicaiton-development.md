---
title: "UG Development project: Web site using Django"
style:  app
date: 2022-07-22 14:46:20
permalink: blog/Django.html
author_profile: true
toc: true
toc_label: "Page Content"

tags:
  - UG Project
  - Development project
  - Django
  - Python
  - Web development
  

header:
  teaser: "/assets/posts/webdjango/python-django.png"
---
![django](/assets/posts/webdjango/django-img.jfif)
## Introduction

Web development became popular due to the widespread accessibility of the web, especially for commerce. Once businesses quickly realized they could offer their products and services on the web, this created a demand for web development that has never slowed down.

Web development can be divided into three major parts:

1. Backend development: This is concerned with business logic, data storage, and processing.
2. Frontend development: This is concerned with how the user interacts with the system and mainly includes user experience (UX) and user interface (UI) design.
3. API/middleware development: This is concerned with how the backend and frontend apps communicate.

This guide will explore developing web apps using the Python framework Django. This framework mainly addresses backend and API/middleware development. It is therefore assumed that you have at least intermediate level knowledge in Python.

## Python Web Development

Web development in Python picked up to bring the data wrangling and processing power of Python to the web. Some popular sites built on Python/Django include Disqus, Instagram, and Mozilla, among others. 

## What is Django?
Django is a high-level Python web framework that enables rapid development of secure and maintainable websites. Built by experienced developers, Django takes care of much of the hassle of web development, so you can focus on writing your app without needing to reinvent the wheel. It is free and open source, has a thriving and active community, great documentation, and many options for free and paid-for support.

Django helps you write software that is:
### Complete
Django follows the "Batteries included" philosophy and provides almost everything developers might want to do "out of the box". Because everything you need is part of the one "product", it all works seamlessly together, follows consistent design principles, and has extensive and up-to-date documentation.

###Versatile
Django can be (and has been) used to build almost any type of website — from content management systems and wikis, through to social networks and news sites. It can work with any client-side framework, and can deliver content in almost any format (including HTML, RSS feeds, JSON, XML, etc).

Internally, while it provides choices for almost any functionality you might want (e.g. several popular databases, templating engines, etc.), it can also be extended to use other components if needed.

### Secure
Django helps developers avoid many common security mistakes by providing a framework that has been engineered to "do the right things" to protect the website automatically. For example, Django provides a secure way to manage user accounts and passwords, avoiding common mistakes like putting session information in cookies where it is vulnerable (instead cookies just contain a key, and the actual data is stored in the database) or directly storing passwords rather than a password hash.

A password hash is a fixed-length value created by sending the password through a cryptographic hash function. Django can check if an entered password is correct by running it through the hash function and comparing the output to the stored hash value. However due to the "one-way" nature of the function, even if a stored hash value is compromised it is hard for an attacker to work out the original password.

Django enables protection against many vulnerabilities by default, including SQL injection, cross-site scripting, cross-site request forgery and clickjacking (see Website security for more details of such attacks).

### Scalable
Django uses a component-based "shared-nothing" architecture (each part of the architecture is independent of the others, and can hence be replaced or changed if needed). Having a clear separation between the different parts means that it can scale for increased traffic by adding hardware at any level: caching servers, database servers, or application servers. Some of the busiest sites have successfully scaled Django to meet their demands (e.g. Instagram and Disqus, to name just two).

### Maintainable
Django code is written using design principles and patterns that encourage the creation of maintainable and reusable code. In particular, it makes use of the Don't Repeat Yourself (DRY) principle so there is no unnecessary duplication, reducing the amount of code. Django also promotes the grouping of related functionality into reusable "applications" and, at a lower level, groups related code into modules (along the lines of the Model View Controller (MVC) pattern).

### Portable
Django is written in Python, which runs on many platforms. That means that you are not tied to any particular server platform, and can run your applications on many flavors of Linux, Windows, and macOS. Furthermore, Django is well-supported by many web hosting providers, who often provide specific infrastructure and documentation for hosting Django sites.

## What does Django code look like?

In a traditional data-driven website, a web application waits for HTTP requests from the web browser (or other client). When a request is received the application works out what is needed based on the URL and possibly information in ```POST``` data or ```GET``` data. Depending on what is required it may then read or write information from a database or perform other tasks required to satisfy the request. The application will then return a response to the web browser, often dynamically creating an HTML page for the browser to display by inserting the retrieved data into placeholders in an HTML template.

Django web applications typically group the code that handles each of these steps into separate files:
![Landing screen](/assets/posts/webdjango/basic-django.png)

## Hello World in Django
To get started with Django, install it using this command on your terminal.

```bash
pip install django
```

To start a new Django project, run the starter command, which creates a boilerplate project.

```bash
django-admin startproject hello_world
```

You now have a Django project with basic boilerplate code. Within a Django project, there can exist several ***apps***.

An app can be described as a library of code representing a discrete part of a larger project. A Django app requires at least one app to run. To create an app, use the ```manage.py``` script and pass the ```startapp``` command, as demonstrated below.

```bash
python manage.py startapp myapp
```
At this point, you have a Django project called ```hello_world``` and, within it, an app called ```myapp```.

## App Boilerplate
The app folder comes with starter files that are critical for any Django app. These are:

1. app.py: Where app configurations are defined
2. admin.py: Where model configurations are defined in relation to the project admin page
3. models.py: Where database tables are defined as ```Models```
4. views.py- Where Django views are defined. These are objects that define how content is displayed on a web page.

For this project, you will add a new file and name it ```urls.py```. Copy the code below into the file under the ```myapp/``` folder.

```python
from django.urls import path
from .views import home
urlpatterns = [
    path('', home,name='home'),
]
```
The function of this file is to define which view will be accessed by a user if they access a certain URL. In this case, when they access the root URL, they will be directed to the home view.

The next step is to develop the ```home``` view. Open ```views.py``` and copy the code block below.

```python
from django.shortcuts import HttpResponse

# Create your views here.
def home(request):
    return HttpResponse("Hello world from Django")
```
The above creates a view called ```home```, which returns an ```HTTPResponse```. This means it will be just plain text. In Django, there are class-based and function-based views. Read more about them here.

The app is now complete but needs to be connected to the main project since at runtime, the user accesses the project at root level and then through URL resolving and is directed to the appropriate app. To connect the app to the main project, add it to the ```INSTALLED_APPS``` list in the ```settings.py``` file in the ```hello_world/``` project folder; also, link it in the main ```urls.py``` file in the project.

To add to the ```INSTALLED_APPS``` list, navigate to the ```settings.py``` file and replace the current list with the list below.


```python
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    # local app
    'myapp',
]
```
To link the project URL to the app URL, navigate to the ```hello_world/urls.py``` file and copy the following code block.

```python
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('myapp.urls'))
]
```
With the second item in the list, you are directing that if there is no parameter from the root URL (path empty), traffic should be directed to the URL's file in the ```myapp``` app. Within the ```myapp``` URL's file, the root URL is resolved to display the ```home``` view. This is how you will display the ```Hello world from Django``` message.

## Running the Project
To run the project, run the command:
```bash
python manage.py runserver
```
This will execute the project using a Web Server Gateway Interface (WSGI) that is inbuilt and necessary to run Python projects on the web. The site is accessible by default on [http://127.0.0.1:8000](http://127.0.0.1:8000).

## Sample Screen
After running the ```runserver``` command, upon accessing the default Django URL, you should see a hello world page similar to the one below.

![Landing screen](/assets/posts/webdjango/django.png)

## Conclusion
Web development in Django is quite a wide field. The skills learned in this guide offer an introduction to what is required for positions such as a backend or full-stack Python/Django web developer. To further build on this guide, research the following aspects of web development using Django:

1. Django Forms: Learn how to collect data from users and pass to Django views and forms for further processing. Get started here
2. Handling static files and upload data: Learn how to handle uploading of files and media. Get started with the official docs
3. Using Django APIs with the Django Rest Framework (DRF): Developing a Django app with API capabilities. Starter tutorial can be found here.
4. Django Databases: Performing database operations and migrating models (Tables). Quickstart guide.
5. Jinja templating engine: Learn how to use Jinja to manipulate HTML code blocks programmatically. Quickstart guide.
6. Deploying a Django app to a live server: Learn how to share your Django app on the cloud. Get started with Django on Digital ocean here.



<p>
{% include  share.html %}
</p>

<span style="color:#9e9696"><i> Last updated: 27/03/2020</i> </span>

<p>
{% include  license.html %}
</p>