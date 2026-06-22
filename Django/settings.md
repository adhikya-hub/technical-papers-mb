# Django Settings File (`settings.py`)

The `settings.py` file contains the configuration for a Django project.

Common settings:

* `SECRET_KEY` - Cryptographic key used for security features.
* `DEBUG` - Enables detailed error pages during development.
* `ALLOWED_HOSTS` - List of allowed domains.
* `INSTALLED_APPS` - Registered Django applications.
* `MIDDLEWARE` - Request/response processing layers.
* `DATABASES` - Database configuration.
* `TEMPLATES` - Template engine settings.
* `STATIC_URL` - Static file URL.

---

## SECRET_KEY

A secret cryptographic key used for:

* Session security
* CSRF token generation
* Password reset tokens
* Signed cookies

Example:

```python
SECRET_KEY = os.environ["SECRET_KEY"]
```

**Never commit the actual secret key to Git.**

---

## Default Django Apps

```python
INSTALLED_APPS = [
    "django.contrib.admin",
    "django.contrib.auth",
    "django.contrib.contenttypes",
    "django.contrib.sessions",
    "django.contrib.messages",
    "django.contrib.staticfiles",
]
```

## App Purposes

| App            | Purpose                        |
| -------------- | ------------------------------ |
| `admin`        | Admin panel                    |
| `auth`         | Authentication and permissions |
| `contenttypes` | Tracks installed models        |
| `sessions`     | User sessions                  |
| `messages`     | Flash messages                 |
| `staticfiles`  | Static file management         |

## Other Built-in Apps

* `django.contrib.sites`
* `django.contrib.sitemaps`
* `django.contrib.humanize`
* `django.contrib.flatpages`
* `django.contrib.redirects`

---

## Middleware

Middleware sits between the browser and your views.

```text
Request
  ↓
Middleware
  ↓
View
  ↓
Middleware
  ↓
Response
```

Default middleware:

```python
MIDDLEWARE = [
    "django.middleware.security.SecurityMiddleware",
    "django.contrib.sessions.middleware.SessionMiddleware",
    "django.middleware.common.CommonMiddleware",
    "django.middleware.csrf.CsrfViewMiddleware",
    "django.contrib.auth.middleware.AuthenticationMiddleware",
    "django.contrib.messages.middleware.MessageMiddleware",
    "django.middleware.clickjacking.XFrameOptionsMiddleware",
]
```

### SecurityMiddleware

Adds security headers and HTTPS-related protections.

### SessionMiddleware

Manages user sessions.

### CommonMiddleware

URL normalization and common HTTP features.

### CsrfViewMiddleware

Protects against CSRF attacks.

### AuthenticationMiddleware

Provides `request.user`.

### MessageMiddleware

Supports temporary notifications.

### XFrameOptionsMiddleware

Protects against clickjacking.

---

## Django Security

### CSRF (Cross-Site Request Forgery)

Tricks a logged-in user into performing an unwanted action.

Example:

```html
<form action="https://bank.com/transfer">
```

### Protection

```html
{% csrf_token %}
```

Validated by `CsrfViewMiddleware`.

---

## XSS (Cross-Site Scripting)

### What is it?

Injection of malicious JavaScript into webpages.

Example:

```html
<script>alert("hack")</script>
```

### Protection

Django templates automatically escape output:

```html
{{ comment }}
```

---

## Clickjacking

### What is it?

Embedding a site inside a hidden iframe and tricking users into clicking.

### Protection

```http
X-Frame-Options: DENY
```

Provided by `XFrameOptionsMiddleware`.

---

## Other Security Features

### SQL Injection Protection

Use the ORM:

```python
User.objects.get(id=1)
```

instead of raw SQL.

### Password Hashing

Passwords are stored as hashes, not plain text.

### ALLOWED_HOSTS

Prevents host-header attacks.

### Secure Cookies

Can be restricted to HTTPS only.

---

## Other Useful Middleware

### LocaleMiddleware

Language selection.

### GZipMiddleware

Compresses responses.

### ConditionalGetMiddleware

Supports browser caching.

### Cache Middleware

Caches responses for better performance.

---

## WSGI (Web Server Gateway Interface)

WSGI is the standard interface between a Python web application and a web server.

Request flow:

```text
Browser
  ↓
Nginx
  ↓
Gunicorn/uWSGI
  ↓
WSGI
  ↓
Django
```

`wsgi.py` exposes the Django application:

```python
from django.core.wsgi import get_wsgi_application

application = get_wsgi_application()
```

## WSGI vs ASGI

| WSGI                 | ASGI                   |
| -------------------- | ---------------------- |
| Synchronous          | Async + Sync           |
| No WebSockets        | Supports WebSockets    |
| Traditional web apps | Real-time applications |

Use **WSGI** for traditional Django applications and **ASGI** when async features or WebSockets are needed.
