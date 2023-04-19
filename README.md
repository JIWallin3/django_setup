# Django Projects - Setup Reference

Standard django project setup information. This is a living document and will change with my preference. It is intended for my reference but made public in case it can help others. I use PyCharm Pro (PC) as my ide. I appreciate the features they have built in and the template project starts

### Project Setup

1. Make sure Postgres is running local
2. Start project in PC
3. Attach initial application for `USERS`
4. Activate virtual environment:
```
venv/Scripts/activate
```
5. Install required packages
```
pip install psycopg2-binary graphene-django python-dotenv
```
6. Settings.py file should have the following imports
```py
  from pathlib import Path
  from dotenv import load_dotenv
  import os
  load_dotenv()
```
7. Make sure to add apps to `INSTALLED_APPS` in `settings.py`
```py
  INSTALLED_APPS = [
    "django.contrib.admin",
    "django.contrib.auth",
    "django.contrib.contenttypes",
    "django.contrib.sessions",
    "django.contrib.messages",
    "django.contrib.staticfiles",
    'graphene_django',  # add graphene_django to INSTALLED_APPS
    'threejuliet.apps.ThreeJulietConfig',  # add threejuliet config app to INSTALLED_APPS
    'chat.apps.ChatConfig', # add chat app to INSTALLED_APPS
  ]
```
8. Setup static files in `settings.py`
```py
  # Static files (CSS, JavaScript, Images)
  # https://docs.djangoproject.com/en/4.2/howto/static-files/

  STATIC_URL = "/static/"
  # Set the STATIC_ROOT setting to a valid filesystem path where Django can collect static files
  STATIC_ROOT = os.path.join(BASE_DIR, 'collected_static')

  MEDIA_URL = '/media/'
  MEDIA_ROOT = os.path.join(BASE_DIR, 'static/media')

  STATICFILES_DIRS = [
    os.path.join(BASE_DIR, 'static')
  ]
```
9. Setup graphene schema in `settings.py`
```py
  # Graphene settings
  GRAPHENE = {
    'SCHEMA': 'chat.schema.schema'
  }
```
