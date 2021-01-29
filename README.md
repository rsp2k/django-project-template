# Template for creating django project template
Used with ``django-admin startapp --template`` command. Reference this repositories .zip file to use:

> ####Example:
> 
> ``django-admin startapp --template`` ``https://github.com/rsp2k/django-project-template/archive/master.zip``

  
## Features
  - ipython==7.19.0
  - Django settings configured by ENVIRONMENT_VARIABLES
  - dj-database-url==0.5.0
    - Defaults to sqllite if DJANGO_DATABASE_URL is not set
  - django-debug-toolbar==3.2
    - Only enabled when DJANGO_DEBUG is true
  - django-extensions==3.1.0
  - django-grappelli==2.14.3
  - django-health-check==3.16.1
  - sentry-sdk==0.19.5
    - Enabled with SENTRY_DSN 
      - Optionally set SENTRY_ENVIRONMENT
  - huey==2.3.0  
  - gunicorn==20.0.4

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
* Uses [django-admin startapp ](https://docs.djangoproject.com/en/3.1/ref/django-admin/)
* [Default app template](https://github.com/django/django/tree/master/django/conf/project_template)