# Template for creating django project template

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
