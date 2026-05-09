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

1. **Create a GitHub Repository**:
   - Go to GitHub and create a new repository.
   - Copy the repository URL (e.g., `https://github.com/yourusername/taskapp.git`).

2. **Push Code to GitHub**:
   ```bash
   git remote add origin https://github.com/yourusername/taskapp.git
   git push -u origin master
   ```

3. **Set Up PythonAnywhere Account**:
   - Create an account at pythonanywhere.com.
   - Note your username (e.g., `yourusername`).

4. **Clone Repository on PythonAnywhere**:
   - Go to the "Consoles" tab and start a Bash console.
   - Run: `git clone https://github.com/yourusername/taskapp.git`
   - This creates `/home/yourusername/taskapp/`.

5. **Create Virtual Environment**:
   - In the Bash console: `mkvirtualenv --python=python3.10 taskenv`
   - Activate: `workon taskenv`
   - Install dependencies: `pip install -r taskapp/requirements.txt`

6. **Set Up Database**:
   - Navigate to the project: `cd taskapp`
   - Run: `python manage.py migrate`

7. **Collect Static Files**:
   - Run: `python manage.py collectstatic --noinput`

8. **Update Settings**:
   - Edit `taskapp/settings.py` and replace `'yourusername.pythonanywhere.com'` with your actual domain.

9. **Create Web App**:
   - Go to the "Web" tab.
   - Click "Add a new web app".
   - Choose "Django" and select Python 3.10.
   - Set source code directory to `/home/yourusername/taskapp`.
   - Set virtualenv to `/home/yourusername/.virtualenvs/taskenv`.

10. **Configure WSGI**:
    - In the web app settings, set WSGI file to `/var/www/yourusername_pythonanywhere_com_wsgi.py`.
    - Edit that file with:
      ```python
      import os
      import sys

      path = '/home/yourusername/taskapp'
      if path not in sys.path:
          sys.path.append(path)

      os.environ['DJANGO_SETTINGS_MODULE'] = 'taskapp.settings'

      from django.core.wsgi import get_wsgi_application
      application = get_wsgi_application()
      ```

11. **Configure Static Files**:
    - In the web app settings, add static file mapping:
      - URL: `/static/`
      - Directory: `/home/yourusername/taskapp/staticfiles`

12. **Reload Web App**:
    - Click "Reload" in the web tab.

Your app should now be live at `https://yourusername.pythonanywhere.com`!