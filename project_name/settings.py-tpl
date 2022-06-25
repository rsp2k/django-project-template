"""
For more information on this file, see
https://docs.djangoproject.com/en/3.1/topics/settings/

For the full list of settings and their values, see
https://docs.djangoproject.com/en/3.1/ref/settings/
"""
import dj_database_url
import os
from pathlib import Path

SENTRY_DSN = os.environ.get("SENTRY_DSN", None)
SENTRY_ENVIRONMENT = os.environ.get("SENTRY_ENVIRONMENT", None)

if SENTRY_DSN:
    import sentry_sdk
    from sentry_sdk.integrations.django import DjangoIntegration

    sentry_sdk.init(
        dsn=SENTRY_DSN,
        environment=SENTRY_ENVIRONMENT,
        integrations=[DjangoIntegration()],
        send_default_pii=True,
    )


# Build paths inside the project like this: BASE_DIR / 'subdir'.
BASE_DIR = Path(__file__).resolve().parent.parent


# Quick-start development settings - unsuitable for production
# See https://docs.djangoproject.com/en/3.1/howto/deployment/checklist/

# SECURITY WARNING: keep the secret key used in production secret!
SECRET_KEY = os.environ.get('DJANGO_SECRET_KEY', '{{ secret_key }}')

# SECURITY WARNING: don't run with debug turned on in production!
DEBUG = (os.environ.get('DJANGO_DEBUG', False) == "True")\
        or os.environ.get('DJANGO_DEBUG', False) == "1"

ALLOWED_HOSTS = []

ALLOWED_HOSTS_ENV = os.environ.get('DJANGO_ALLOWED_HOSTS', '*')
if ALLOWED_HOSTS_ENV:
    for host in ALLOWED_HOSTS_ENV.split(','):
        ALLOWED_HOSTS.append(host)


# Application definition

INSTALLED_APPS = [
    'grappelli.dashboard',
    'grappelli',
    'filebrowser',
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',

    'allauth',
    'allauth.socialaccount',
    'allauth.socialaccount.providers.google',
    
    'django_extensions',
    'health_check',
    'health_check.db',
    'health_check.cache',
    'health_check.storage',
    'health_check.contrib.migrations',
    'health_check.contrib.redis',
    'debug_toolbar',
    
    'huey.contrib.djhuey',
    'bx_django_utils',
    'huey_monitor',
    
    'django_fsm',
    'fsm_admin',
    'django_fsm_log',
    
    'reversion',
    'nested_admin',
    
    'crispy_forms',
    'crispy_bootstrap5',

    'user_visit',
    'django_tables2',
    'bootstrap5',
    'django_bootstrap_icons',
    'menu',
    'accounts',
]

MIDDLEWARE = [
    'debug_toolbar.middleware.DebugToolbarMiddleware',
    'django.middleware.security.SecurityMiddleware',
    'django.contrib.sessions.middleware.SessionMiddleware',
    'django.middleware.common.CommonMiddleware',
    'django.middleware.csrf.CsrfViewMiddleware',
    'django.contrib.auth.middleware.AuthenticationMiddleware',
    'django.contrib.messages.middleware.MessageMiddleware',
    'django.middleware.clickjacking.XFrameOptionsMiddleware',
    'user_visit.middleware.UserVisitMiddleware',
]

ROOT_URLCONF = '{{ project_name }}.urls'

TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [
            os.path.join(BASE_DIR, "templates"),
        ],
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]

WSGI_APPLICATION = '{{ project_name }}.wsgi.application'


# Database
# https://docs.djangoproject.com/en/3.1/ref/settings/#databases
# Using dj-database-url for ease of cramming everything into one env variable
# https://github.com/jacobian/dj-database-url
DATABASE_URL = os.environ.get('DJANGO_DATABASE_URL', 'sqlite://')

DATABASES = {
    'default': dj_database_url.config()
}
#        conn_max_age=os.environ.get('DJANGO_DATABASE_CONN_MAX_AGE', None),
#        ssl_require=os.environ.get('DJANGO_DATABASE_SSL_REQUIRE', False),
#    ),
#}

REDIS_URL = os.environ.get('DJANGO_REDIS_URL', 'redis://redis:6379')

# https://docs.djangoproject.com/en/3.1/ref/settings/#email-backend

CACHES = {
    "default": {
        "BACKEND": "django_redis.cache.RedisCache",
        "LOCATION": REDIS_URL + "/?db=1",
        "OPTIONS": {"CLIENT_CLASS": "django_redis.client.DefaultClient"},
    }
}

SESSION_ENGINE = "django.contrib.sessions.backends.cache"
SESSION_CACHE_ALIAS = "default"

if DEBUG:
    # Dont send emails in dev
    EMAIL_BACKEND = "django.core.mail.backends.dummy.EmailBackend"
else:
    EMAIL_BACKEND = "djhuey_email.backends.HueyEmailBackend"
    #MAIL_BACKEND = "django.core.mail.backends.smtp.EmailBackend"
    HUEY_EMAIL_BACKEND = "django.core.mail.backends.smtp.EmailBackend"

EMAIL_HOST = os.environ.get('DJANGO_EMAIL_HOST')
EMAIL_PORT = int(os.environ.get('DJANGO_EMAIL_PORT', 25))

# Password validation
# https://docs.djangoproject.com/en/3.1/ref/settings/#auth-password-validators

AUTH_PASSWORD_VALIDATORS = [
    {
        'NAME': 'django.contrib.auth.password_validation.UserAttributeSimilarityValidator',
    },
    {
        'NAME': 'django.contrib.auth.password_validation.MinimumLengthValidator',
        'OPTIONS': {'min_length': 3},
    },
    {
        'NAME': 'django.contrib.auth.password_validation.CommonPasswordValidator',
    },
    {
        'NAME': 'django.contrib.auth.password_validation.NumericPasswordValidator',
    },
]

AUTHENTICATION_BACKENDS = [
    # Needed to login by username in Django admin, regardless of `allauth`
    "django.contrib.auth.backends.ModelBackend",
    # `allauth` specific authentication methods, such as login by e-mail
    "allauth.account.auth_backends.AuthenticationBackend",
]

SITE_ID = 1

SOCIALACCOUNT_PROVIDERS = {
    "google": {
        "SCOPE": [
            "profile",
            "email",
        ],
        "APP": {
            "client_id": os.environ.get("GAUTH_CLIENT_ID", None),
            "secret": os.environ.get("GAUTH_SECRET", None),
            "key": os.environ.get("GAUTH_KEY", None),
        },
    }
}


# Internationalization
# https://docs.djangoproject.com/en/3.1/topics/i18n/

LANGUAGE_CODE = os.environ.get('DJANGO_LANGUAGE_CODE', 'en-us')

TIME_ZONE = os.environ.get('DJANGO_TIME_ZONE', 'UTC')

USE_I18N = True

USE_L10N = True

USE_TZ = True

DEFAULT_AUTO_FIELD = "django.db.models.AutoField"

# Static files (CSS, JavaScript, Images)
# https://docs.djangoproject.com/en/3.1/howto/static-files/
STATIC_URL = os.environ.get(
    'DJANGO_STATIC_URL',
    '/static/'
)
STATIC_ROOT = os.environ.get(
    'DJANGO_STATIC_ROOT',
    os.path.join(
        BASE_DIR,
        'run',
        'static'
    )
)

# Media files (uploaded w/POST request, imported from shell)
# https://docs.djangoproject.com/en/3.1/topics/files/
MEDIA_URL = os.environ.get(
    'DJANGO_MEDIA_URL',
    '/media/'
)
MEDIA_ROOT = os.environ.get(
    'DJANGO_MEDIA_ROOT',
    os.path.join(
        BASE_DIR,
        'run',
        'media'
    )
)


def show_toolbar(request):
    if DEBUG:
        return True


DEBUG_TOOLBAR_CONFIG = {"SHOW_TOOLBAR_CALLBACK": show_toolbar}

if DEBUG:
    # Allow ./manage.py shell_plus --notebook to query models https://code.djangoproject.com/ticket/31056
    os.environ["DJANGO_ALLOW_ASYNC_UNSAFE"] = "true"


HEALTH_CHECK = {"DISK_USAGE_MAX": 60, "MEMORY_MIN": 2000}  # percent  # in MB

GRAPPELLI_ADMIN_TITLE = os.environ.get("DJANGO_SITE_TITLE", "Admin Site")
GRAPPELLI_AUTOCOMPLETE_LIMIT = 20
GRAPPELLI_INDEX_DASHBOARD = "{{ project_name }}.dashboard.CustomIndexDashboard"
GRAPPELLI_SWITCH_USER = True

# Huey
pool = ConnectionPool(
    host="redis",
    port=os.environ.get("REDIS_LISTEN_PORT", 6379)
    max_connections=100,
)

HUEY = RedisHuey(
    os.environ.get("PROJECT_NAME"), 
    connection_pool=pool,
)

AUTH_USER_MODEL = "accounts.user"

## Django allauth
ACCOUNT_USER_MODEL_USERNAME_FIELD = None
ACCOUNT_EMAIL_REQUIRED = True
ACCOUNT_USERNAME_REQUIRED = False
ACCOUNT_AUTHENTICATION_METHOD = "email"

ACCOUNT_ADAPTER = "accounts.adapter.AccountAdapter"
SOCIALACCOUNT_ADAPTER = "accounts.adapter.CheckSignupDomainModel"

# https://django-crispy-forms.readthedocs.io/en/latest/crispy_tag_forms.html#make-crispy-forms-fail-loud
CRISPY_FAIL_SILENTLY = not DEBUG
CRISPY_ALLOWED_TEMPLATE_PACKS = "bootstrap5"
CRISPY_TEMPLATE_PACK = "bootstrap5"

FILEBROWSER_EXTENSIONS = {
    "Image": [".jpg", ".jpeg", ".gif", ".png", ".tif", ".tiff"],
    "Document": [".pdf", ".doc", ".rtf", ".txt", ".xls", ".csv", ".docx"],
    "Video": [".mov", ".mp4", ".m4v", ".webm", ".wmv", ".mpeg", ".mpg", ".avi", ".rm"],
    "Audio": [".mp3", ".wav", ".aiff", ".midi", ".m4p"],
    "Terraform": [".tf", ".hcl", ".json", ".tfvars", ".tfvars.json"],
    "Markdown": [
        ".md",
    ],
}
FILEBROWSER_SELECT_FORMATS = {
    "file": ["Image", "Document", "Video", "Audio"],
    "image": ["Image"],
    "document": ["Document", "Markdown"],
    "media": ["Video", "Audio"],
}
