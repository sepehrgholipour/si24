# DirectAdmin deployment

Create a Python application for `si24seller.app` with the project directory as
the application root and `passenger_wsgi.py` as the startup file.

Install dependencies and initialize the database:

```bash
pip install -r requirements.txt
python manage.py migrate
python manage.py collectstatic --noinput
```

Set these environment variables in DirectAdmin:

```text
DJANGO_DEBUG=false
DJANGO_SECRET_KEY=<long-random-secret>
DJANGO_ALLOWED_HOSTS=si24seller.app,www.si24seller.app
DJANGO_CSRF_TRUSTED_ORIGINS=https://si24seller.app,https://www.si24seller.app
```

Restart the Python application after saving the variables. Enable a Let's
Encrypt certificate for both the root and `www` domain before testing HTTPS.
