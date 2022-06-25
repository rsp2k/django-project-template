# Template for creating django project template
Used with ``django-admin startapp --template`` command. Reference this repositories .zip file to use:

> ####Example:
> 
> ``django-admin startapp --template`` ``https://github.com/rsp2k/django-project-template/archive/master.zip``

## Provides
* Django 4
  - Development Tools
    - [django-debug-toolbar](https://django-debug-toolbar.readthedocs.io/en/latest/) Help for django developers
    - [django-extensions](https://django-extensions.readthedocs.io/en/latest/) Tools for making admin operations easier
    - [grapviz model visualization](https://django-extensions.readthedocs.io/en/latest/graph_models.html) Visualize data models
    - [django-dirtyfields](hthttps://django-debug-toolbar.readthedocs.io/en/latest/tps://django-dirtyfields.readthedocs.io/en/latest/advanced.html) Used to maintain slugfield
    - [django-crispyforms](https://django-crispy-forms.readthedocs.io/en/latest/) Render nice looking bootstrap forms with no effort
    - [crispy-bootstrap5](https://github.com/django-crispy-forms/crispy-bootstrap5) Crispy forms templates for bootstrap5 forms
    - [django-allauth](https://django-allauth.readthedocs.io/en/latest/) Social Authentication
    - [django-reversion](https://django-reversion.readthedocs.io/) Version Control / rollback for models
    - [django-user-visit](https://github.com/yunojuno/django-user-visit) Records daily user visits
    - [django-fernetfields](https://github.com/rsp2k/django-fernet-fields) Encrypt model fields using settings.SECRET_KEY
    - [django-bootstrap-v5](https://github.com/zelenij/django-bootstrap-v5/) Bootstrap 5
    - [django-bootstap-icons](https://github.com/christianwgd/django-bootstrap-icons) Bootstrap icons
    - [django-simple-menu](https://django-simple-menu.readthedocs.io/)  define multiple menus using straight forward python code in each of your installed apps

  - Admin Enhancements
    - [Grappelli](https://django-grappelli.readthedocs.io/en/latest/) Nice theme, Inline sortables, Autocomplete
  - Finite State Machine
    - [django-fsm](https://github.com/gadventures/django-fsm-admin) finite state machine integration for Django models
    - [django-fsm-log](https://github.com/jazzband/django-fsm-log) show state changes
    - [fsm-admin](https://github.com/gadventures/django-fsm-admin) Add actions to admin page to change state
  - Task Queue
    - [huey](https://huey.readthedocs.io/en/latest/) Task Queue
    - [django-huey-monitor](https://github.com/boxine/django-huey-monitor) Monitor the Queue
  - Operations/Infrastructure
    - [django-health-check](https://github.com/KristianOellegaard/django-health-check) Status page
    - [sentry](https://sentry.io/) Error logging and reporting
    - [iPython](https://ipython.org) Completion, etc... Make python command line fun!
- HTTP
  - Front End (Reverse Proxy) / SSL
    - [Caddy](https://github.com/caddyserver/caddy) front-end HTTPS server
    -

  - WSGI
    - [Gunicorn](https://github.com/benoitc/gunicorn) WSGI (HTTP/1.1)

  - ASGI
    - [Uvicorn](https://www.uvicorn.org/) ASGI (WebSockets)
    - **TODO** consider using Uvicorn for WSGI also

- Database
  - [PostgreSQL Database](https://postgresql.org) Relational Database
  - [PGAdmin](https://pgadmin.org) Postgres Admin Interface


* [Redis](https://redis.io/) key=value store
* [Mailcatcher](https://mailcatcher.me/) Receive any SMTP message and display in browser


## Steps to deploy

1. Create a new project repo
   - Use github/gitlab
2. Checkout the repository you just created (do it in PyCharm or another IDE, get with the times Boomer!)
3. Create a virtualenv, and pip install the requirements file
4. Create a django project using the [best Django template around](https://gitlab.com/rpmrpm/django_project_template)
   >```python3 manage.py startproject --template https://gitlab.com/rpmrpm/django_project_template __PROJECT_NAME__ .```
5. Add apps to requirements.txt, INSTALLED_APPS (settings.py), urls.py etc..
5. Start the docker containers
   >```docker-compose up ```
6. Happy Development!

## References
* Uses [django-admin startapp ](https://docs.djangoproject.com/en/3.1/ref/django-admin/#startapp)
* [Default app template](https://github.com/django/django/tree/master/django/conf/project_template)
