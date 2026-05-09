# Task App

A simple task management app built with Django.

## Features

- Create, read, update, delete tasks
- Mark tasks as completed
- Toggle task status

## Local Development

1. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
2. Run migrations:
   ```bash
   python manage.py migrate
   ```
3. Start the development server:
   ```bash
   python manage.py runserver
   ```
4. Open `http://127.0.0.1:8000/` in your browser.

## Deploy to Render

1. Push your project to GitHub.
2. Create a new Web Service on Render and connect your repo.
3. Set the build command to:
   ```bash
   pip install -r requirements.txt
   python manage.py migrate
   python manage.py collectstatic --noinput
   ```
4. Set the start command to:
   ```bash
   gunicorn taskapp.wsgi --log-file -
   ```
5. Set environment variables on Render:
   - `DEBUG=False`
   - `DJANGO_ALLOWED_HOSTS` to your Render service domain
   - `DATABASE_URL` if you add a Postgres database service
6. Deploy and visit the Render URL.

### Notes

- `Procfile` is included for Render so the app starts with Gunicorn.
- If you want to use a managed database, add a Render Postgres service and paste its `DATABASE_URL` into Render settings.
