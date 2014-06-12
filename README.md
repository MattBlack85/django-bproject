django-bproject part 2
===============

Apps
---------------
Time to write some stuff, a typical django project is divided into one or more apps. An app is an
application that actually does something concrete, like a blog or a file upload. You could plug
an app into another project and it should work out of the box. Just copy paste and adjust your urls
file.

To create our first app let's type in our console (be sure to be in the folder where you have manage.py
file) `python manage.py startapp articles`
Notice that now we have one more folder `articles` in our project and inside it we can find the following
files:
 * admin.py
 * __init__.py
 * models.py
 * views.py
 * tests.py
