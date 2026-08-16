# django-project-example

Boilerplate Django Application for Learning and Development. The intent is to set up CI/CD, IAC, and containerisation for further understanding of the framework usage.

```shell
# initialise uv project
uv init

# add dependencies
uv add django
uv add ruff --group dev

# verify django version
uv run django-admin --version

# create project - add . to stop django creating extra nested folder
uv run django-admin startproject <project name> .

# test run the server
uv run python manage.py runserver

# Note: if port 8000 (default) is already in use - address either by:
uv run python manage.py runserver <port>

# manage.py before `execute_from_command_line`
from django.core.management.commands.runserver import Command as runserver
runserver.default_port = "8080"

# create app within project - app = web application for specific context e.g. home page, members DB, etc
cd <project name>
uv run python manage.py startapp <app name> (e.g. members)

# Should now have another folder called members within the project
```
