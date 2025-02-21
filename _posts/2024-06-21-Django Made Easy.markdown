---

layout: single
title:  "Django made easy!"
date:   2024-02-06 14:46:24 +0100
published: false
---

## Getting started with Django with basic python knowledge 

### Overview
* Open source Python Web Framework
* Server Side framework
* MVT architectural pattern, lightweight
* Faster development with basic python knowledge
* Introduced in 2 July 2005 , Latest release when writing this blog : 7 May 2024
* Batteries included
* Frontend can be build in HTML+ CSS, React, Angular , Vue
* What you can build with Django ? - Backend API, Mobile apps, webapp, website
* Building API with Django = django framework  + django REST framework
* Other Famework : Flask, CherryPie, Web2Py, Pyramid

### Setup
* Install Python
* Create Virtual Enviorment `install virtualenv`
* Actiavte virtial Enviorment `<path of project dir>\env\scripts\activate`
 Note: You can install all required python packages within this local project enviorment. if you want to install globally, then just deactivate virtual enviorment using
 `<path of project dir>\env\scripts\dectivate`
* install `pip install django` (best way to use virtual env). type `pip list` to check instaled packed
* `django-admin` to list all django commands
* To create Project `django-admin startproject <project-name>`
* cd into project-name directory
* Run this run project `python manage.py runserver`



### MVT Architectural Style

Model: The Model is going to act as the interface of your data. It is responsible for maintaining data. It is the logical data structure behind the entire application and is represented by a database (generally relational databases such as MySql, Postgres).

View: The View is the user interface that you see in your browser when you render a website. It is represented by HTML/CSS/Javascript and Jinja files.

Template: A Template consists of static parts of the desired HTML output as well as some special syntax describing how dynamic content will be inserted.

Reference - 
https://dev.to/sm0ke/django-tutorial-mvt-architecture-custom-commands-19nb
https://www.geeksforgeeks.org/django-project-mvt-structure/


### Basic Web Project


  
