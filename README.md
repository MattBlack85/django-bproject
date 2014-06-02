django-bproject part 1
===============

Setup and run!
--------------

So we want to build a Django-powered application. Before starting we need some
tools, assure the following things are installed on your pc:
  * pip (it makes life easier)
  * Django
  * Python
  * virtualenv
  * PostgreSQL
  * psycopg2 (PostgreSQL database adapter for Python)

If you don't have Python installed, do that first. Most of Linux distros come
out today with pre-installed Python, if you are on Windows download the .exe (2.7
version) and do the rest of the job.

Now we should install pip; pip is a tool for installing easily Python packages, if
you run Linux you can probably install it from your package manager, if you're
running something else you should read this https://pip.pypa.io/en/latest/installing.html

Now that we have pip installed we can do the rest of the job easily, let's go ahead!

Fire your console and type:
`pip install virtualenv`

virtualenv creates a virtual environment where we can mess around without caring to break something (if
everything is done correctly, of course!)

Let's create a folder for our project, let's call it django-bproject. Initialize the django-project typing 
`django-admin.py startproject bproject django-bproject`
the last two arguments are respectively the name of the folder where will live the "core" structure
of our project and the folder where we want to initialize the django project. If you don't have a folder
omit the last argument, in this case django-admin.py script will create a new one.

Good job! Now the folder django-bproject should look like:

django-bproject/
               |
               |
               manage.py
               bproject/
                       |
                       |
		       __init__.py
		       settings.py
		       urls.py
		       wsgi.py



Let's now install a virtualenv inside our folder, type `virtualenv path/to/your/django-bproject` where of course
you should write your own path to the folder created some minutes ago instead of path/......

We can now work in the virtualenv, to try it enter the folder django-bproject and type `. bin/activate`. You should
see the name of your app into (), that indicates that you're into another environment.

Settings
----------
Now we have to tweak some settings in order to procede. In the folder `bproject` there is a `settings.py` file, open
it and ignore almost everything, for now look at SECRET_KEY and DATABASES and INSTALLED_APPS variables.
* SECRET_KEY: is a secret and should remain secret, it's created automatically (and randomly) by django and it provides
  cryptographic signing, don't share it for any reason with anyone.
* DATABASES: here we can pass data to connect to our db, default values are for SQLite so we have to change them because
  we are going to use PostgreSQL, set ENGINE to `'django.db.backend.postgresql_psycopg2'`, set NAME to `'bpro_test'`,
  set USER to `'buser'`. There are other settings but we are not going to use it for this tutorial, if you want know more
  take a look at https://docs.djangoproject.com/en/1.6/ref/settings/#databases
* INSTALLED_APPS: we won't touch it for know, but remember that if you are going to create apps for your poject (`python
  manage.py startapp appname`) you should add it to INSTALLED_APPS, we will see why later.
