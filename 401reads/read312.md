# Library Website and API
* We cannot build a web API with only Django Rest Framework; it always must be added to a project after Django itself has been installed and configured.

* The most important differences is that Django creates websites containing webpages, while Django REST Framework creates web APIs which are a collection of URL endpoints containing available HTTP verbs that return JSON.

* we will build out a basic Library website with traditional Django and then extend it into a web API with Django REST Framework.


## Traditional Django
### First we need to create a django ptoject and Run migrate to sync the database with Django’s default settings and start up the local Django web server.
```bash 
$ cd ~/Desktop
$ mkdir code && cd code
$ mkdir library && cd library
$ pipenv install django~=3.1.0
$ pipenv shell
(library) $ django-admin startproject config .
(library) $ python manage.py migrate
(library) $ python manage.py runserver
```

* __init__.py is a Python way to treat a directory as a package; it is empty
* asgi.py stands for Asynchronous Server Gateway Interface and is a new option in Django 3.0+
* settings.py contains all the configuration for our project
* urls.py controls the top-level URL routes
* wsgi.py stands for Web Server Gateway Interface and helps Django serve the eventual web pages
* manage.py executes various Django commands such as running the local web server or creating a new app.
Run migrate to sync the database with Django’s default settings and start up the local Django web server.


### First app
The typical next step is to start adding apps, which represent discrete areas of functionality. A single Django project can support multiple apps.

Stop the local server by typing Control + c  then :
```bash
(library) $ python manage.py startapp books
``` 
* There are 6 new files created:

1. admin.py is a configuration file for the built-in Django Admin app
2. apps.py is a configuration file for the app itself
the migrations/ directory stores migrations files for database changes
3. models.py is where we define our database models
4. tests.py is for our app-specific tests
5. views.py is where we handle the request/response logic for our web app
6. __init__.py and it is empty 
* Typically developers will also create an urls.py file within each app too for routing.
 
1. Open the config/settings.py file,then add the new app to our INSTALLED_APPS configuration. 

# library_project/settings.py
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',

    # Local
    'books', # new
]
2. run migrate to sync our database with the changes.

(library) $ python manage.py migrate

### App progress 
Each web page in traditional Django requires several files: a view, url, and template. But first we need a database model so let’s start there.

#### **1. Models**
open up the file books/models.py and update it as follows:

# books/models.py
from django.db import models
```python 
class Book(models.Model):
    title = models.CharField(max_length=250)
    subtitle = models.CharField(max_length=250)
    author = models.CharField(max_length=100)
    isbn = models.CharField(max_length=13)

    def __str__(self):
        return self.title
```

1. import models from Django on the top line
2. create a Book class that extends it.
3. add four fields: title, subtitle, author, and isbn. 
4. a __str__ method so that the title of a book will display in the admin later on.


* Since we created a new database model we need to create a migration file to go along with it, then update our database.

#### **2. Admin**
before we start entering data into our new model via the built-in Django app, we must do two things 
1. create a superuser account 

Start with the superuser account. 
```bash
(library) $ python manage.py createsuperuser
```
2. update our book app’s admin.py file.
```python 

from django.contrib import admin
from .models import Book
admin.site.register(Book)
``` 

#### **3. Views**
The views.py file controls how the database model content is displayed.

1. Update the books/views.py file.

```python 
from django.views.generic import ListView
from .models import Book

class BookListView(ListView):
    model = Book
    template_name = 'book_list.html'
``` 
* On the top lines we’ve imported ListView and our Book model. 
* we create a BookListView class that specifies the model to use and the template.

#### **4. URLs**
We need to set up both the project-level urls.py file and then one within the books app.
* In project URL 
```python 

from django.contrib import admin
from django.urls import path, include # new

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('books.urls')), # new
]
``` 
* The top two lines import the built-in admin app, path for our routes, and include which will be used with our books app. 
If a user goes to /admin/ they will be redirected to the admin app. 

* configure books/urls.py file.
```python 
from django.urls import path

from .views import BookListView

urlpatterns = [
    path('', BookListView.as_view()),
]
``` 

* We import our views file and then configure BookListView at the empty string '' again.



#### **4. Template**
1. create a separate  project-level templates directory  within it  create a books folder, and then a book_list.html file. Finally update our settings.py file to point there.

```html
<!-- books/templates/books/book_list.html -->
<h1>All books</h1>
{% for book in object_list %}
  <ul>
    <li>Title: {{ book.title }}</li>
    <li>Subtitle: {{ book.subtitle }}</li>
    <li>Author: {{ book.author }}</li>
    <li>ISBN: {{ book.isbn }}</li>
  </ul>
{% endfor %}
``` 
* Django ships with a template language that allows for basic logic. 
1. we use the for tag to loop over all available books. 
2. Template tags must be included within opening/closing brackets and parentheses. 

* The name of this object is object_list,so our loop will be
```html
{% for book in object_list %}
{% endfor %}
```

* Now we can start up the local Django server and see our web page.

## Django REST Framework
### Adding Django REST Framework
1. Django REST Framework is added just like any other third-party app.

Then on the command line type the below.
```bash
(library) $ pipenv install djangorestframework~=3.11.0
```
2. Add it to the INSTALLED_APPS config in our settings.py file. 

<!-- our API will expose a single endpoint that lists out all books in JSON. So we will need a new URL route, a new view, and a new serializer file.

There are multiple ways we can organize these files however my preferred approach is to create a dedicated api app. That way even if we add more apps in the future, each app can contain the models, views, templates, and urls needed for dedicated webpages, but all API-specific files for the entire project will live in a dedicated api app. -->
## A new API app
1. first create a new api app.
```bash 
(library) $ python manage.py startapp api
```
2. Then add it to INSTALLED_APPS.

### 1. Modal 
The api app will not have its own database models so there is no need to create a migration file and run migrate to update the database.

### 2. URLs
Adding an API endpoint is just like configuring a traditional Django app’s routes. 
1.  at the project-level we need to include the api app and configure its URL route, which will be api/.

2. create a urls.py file within the api app.And update it as follows:


### 3. Views
view relies on Django REST Framework’s built-in generic class views.

* Update views.py file to look like the following:
```python 

from rest_framework import generics
from books.models import Book
from .serializers import BookSerializer

class BookAPIView(generics.ListAPIView):
    queryset = Book.objects.all()
    serializer_class = BookSerializer

``` 
* On the top lines we import Django REST Framework’s generics class of views, the models from our books app, and serializers from our api app (we will make the serializers next).

* Then we create a BookAPIView that uses ListAPIView to create a read-only endpoint for all book instances.


#### **Serializers**
A serializer translates data into a format that is easy to consume over the internet, typically JSON, and is displayed at an API endpoint.

1. Make a serializers.py file within our api app.

2. Update it as follows in api/serializers.py.
```python 
from rest_framework import serializers

from books.models import Book

class BookSerializer(serializers.ModelSerializer):
    class Meta:
        model = Book
        fields = ('title', 'subtitle', 'author', 'isbn')

```
* On the top lines we import Django REST Framework’s serializers class and the Book model from our books app. 
* We extend Django REST Framework’s ModelSerializer into a BookSerializer class that specifies our database model Book and the database fields we wish to expose: title, subtitle, author, and isbn.

## cURL
We can use the popular cURL program to execute HTTP requests via the command line. All we need for a basic GET request it to specify curl and the URL we want to call.

## Browsable API
Django REST Framework provides this visualization by default. And there is a lot of functionality built into this page

[<= Back](read31.md)
