# Task App

A simple task management app built with Django.

## Features

- Create, read, update, delete tasks
- Mark tasks as completed
- Toggle task status

## Local Development

1. Install dependencies: `pip install -r requirements.txt`
2. Run migrations: `python manage.py migrate`
3. Run server: `python manage.py runserver`

## Deployment on PythonAnywhere

1. Create a PythonAnywhere account.
2. Upload your code to PythonAnywhere (use Git or manual upload).
3. Set up a new web app with Django.
4. In the web app configuration:
   - Set the source code path to your project directory.
   - Set the WSGI configuration file to `taskapp/wsgi.py` (modify it for PythonAnywhere).
   - Set the virtualenv path.
   - Set static files URL to `/static/` and path to `staticfiles/`.
5. Update `taskapp/settings.py`:
   - Set `DEBUG = False`
   - Add your PythonAnywhere domain to `ALLOWED_HOSTS`
   - Configure database if using MySQL/PostgreSQL.
6. Run migrations on PythonAnywhere.
7. Reload the web app.

### WSGI Configuration

For PythonAnywhere, your `taskapp/wsgi.py` should look like:

```python
import os
import sys

path = '/home/yourusername/yourprojectname'
if path not in sys.path:
    sys.path.append(path)

os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'taskapp.settings')

from django.core.wsgi import get_wsgi_application
application = get_wsgi_application()
```

Replace `yourusername` and `yourprojectname` accordingly.