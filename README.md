# How to Setup your Django project with a local_settings.py
# for your development environment - Quick and Clean
### Glen Baker - iepathos@gmail.com
#### I learned this method from django-workshop.de

+ django-admin.py startproject djsetuplocal
+ cd djsetuplocal/djsetuplocal

## Edit settings.py
### djsetuplocal/djsetuplocal/settings.py
'''python
import os
SITE_ROOT = os.realpath.realpath(os.path.dirname(__file__))

DEBUG = False
'''

# delete TEMPLATE_DEBUG = DEBUG

# At the bottom of settings.py, below Logging
'''python
try:
  from local_settings import *
except ImportError:
  pass
'''

## Enter all local development environment information below
### dj/setuplocal/djsetuplocal/local_settings.py
#### Grabs the site root setup in settings.py
'''python
import os
from settings import SITE_ROOT

DEBUG = True
TEMPLATE_DEBUG = DEBUG

# sqlite is the quick an easy development db
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3', # Add 'postgresql_psycopg2', 'mysql', 'sqlite3' or 'oracle'.
        'NAME': os.path.join(SITE_ROOT, 'djlocal.db'),                      # Or path to database file if using sqlite3.
        'USER': '',                      # Not used with sqlite3.
        'PASSWORD': '',                  # Not used with sqlite3.
        'HOST': '',                      # Set to empty string for localhost. Not used with sqlite3.
        'PORT': '',                      # Set to empty string for default. Not used with sqlite3.
    }
}
'''

And you're good to go.  Enter new local development databases into local_settings.py.
create .gitignore file in djsetuplocal
'''text
*.pyc
*.pyo
.installed.cfg
bin
develop-eggs
dist
downloads
eggs
parts
src/*.egg-info
lib
lib64
local_settings.py
*~
'''
