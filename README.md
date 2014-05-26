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
`pip install virtualenv` (or probably `sudo pip install virtualenv` on Linux)

virtualenv creates a virtual environment where we can mess around without caring to break something (if
everything is done correctly, of course!)

Let's create a folder for our project, let's call it django-bproject. Let's now install a virtualenv
inside our folder, type `virtualenv path/to/your/django-bproject` where of course
you should write your own path to the folder created some minutes ago instead of path/......
You should now see 4 additional folders inside django-bproject one:
    * bin
    * include
    * lib
    * lib64

Let's now install Django! Activate first the virtualenv typing `. bin/activate` (note: you should be into
django-bproject folder when typing that command), now that virtualenv is active type `bin/pip install django`.
The command will install Django ONLY inside your virtualenv, this is particulary useful if you are going to
manage different project with different dependencies/Django versions. If you want to exit the virtualenv
just type `deactivate` in your console.

If you are not into django-bproject folder enter it, it's now time to django-initialize our project
typing `bin/django-admin.py startproject bproject .`, the last two arguments are respectively the name
of the folder where will live the "core" structure of our project and the folder where we want to initialize
the django project (. in this case is the folder where we are, so it should be django-bproject. If you haven't
created a folder yet, you can omit the last argument, in this case django-admin.py script will create a new one
with the same name of the project.

Good job! Now the folder django-bproject should look like:

![structure](http://s28.postimg.org/65b32s41p/struc.png)


We are ready to move on, the preparation has been quite long, but it teached you lot of basic concepts you will
use quite often during your (hope long :) ) trip with Django.

Settings
----------
Now we have to tweak some settings in order to proceed. In the folder `bproject` there is a `settings.py` file, open
it and ignore almost everything, for now look at SECRET_KEY and DATABASES and INSTALLED_APPS variables.
* SECRET_KEY: is a secret and should remain secret, it's created automatically (and randomly) by django and it provides
  cryptographic signing, don't share it for any reason with anyone.
* DATABASES: here we can pass data to connect to our db, default values are for SQLite so we have to change them because
  we are going to use PostgreSQL, set ENGINE to `'django.db.backend.postgresql_psycopg2'`, set NAME to `'bpro_test'`,
  set USER to `'buser'`. There are other settings but we are not going to use it for this tutorial, if you want know more
  take a look at https://docs.djangoproject.com/en/1.6/ref/settings/#databases
* INSTALLED_APPS: we won't touch it for know, but remember that if you are going to create apps for your poject (`python
  manage.py startapp appname`) you should add it to INSTALLED_APPS, we will see why later.

PostgreSQL initial setup
----------
Before next lines, you should assure that your postgres instance is configured and it's running. To configure it
you should run the command `postgresql-setup initdb`; to start the server it depends a lot on your OS.

We should now create a database and a user for our database, open your console and type `psql -U postgres`, now we are into
postgresql console, let's create our user:
 * `CREATE ROLE buser;`

this comand will create the user for us, now let's create the database and let's assing the ownership to our `buser`:
 * `CREATE DATABASE bpro_test OWNER buser;`

Don't forget to leave postgres console with `\q` before proceeding

Sync & go
----------
Well done! We are ready to start making awesome stuff. We are going to create some tables, but without writing any sql
for now; open your console, assure that you're in the project folder and type `python manage.py syncdb`

You should see an output like this:
![syncdb](http://s29.postimg.org/4ieulqic7/My_Screenshot.png)

syncdb command runs under the scene SQL to create tables, nice uh? All job done with 0 lines of raw sql.



We are done for now, if everything's ok and your project structure/content is the same of the part 1 branch of this
tutorial (except folder bin/ lib/ lib64/ and include/ because I'm not going to upload them to github) you are ready
for part 2!
