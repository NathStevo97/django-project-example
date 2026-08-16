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

Add views: views = python functions to handle html requests/responses
Django web pages utilise multiple views with different tasks and missions

Sample view:

```python
# project/app/views.py

from django.shortcuts import render
from django.http import HttpResponse


def members(request):
    return HttpResponse("Hello world!")
```

## URLs: Linking Up A View

Add `urls.py` to `<app>` at the same level of `views.py` - sample urls below

```
from django.urls import path
from . import views

urlpatterns = [
    path('members/', views.members, name='members'),
]
```

Above URLs file for members app is app-specific, for root project app, need to add another `urls.py` file to link up `urls.py` from other apps - sample for `<project>/urls.py`

```python
from django.contrib import admin
from django.urls import include, path

urlpatterns = [
    path("", include("members.urls")),
    path("admin/", admin.site.urls),
]
```

Verify via `127.0.0.1:<port>/members`
