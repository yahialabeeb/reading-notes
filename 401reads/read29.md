# Django Best Practices

## setup
1. create and navigate into a dedicated directory called accounts for our code
2. install Django
3. make a new Django project called config
4. make a new app accounts
5. start the local web server
```bash
$ mkdir accounts && cd accounts
$ pipenv install django~=3.1.0
$ pipenv shell
(accounts) $ django-admin.py startproject config .
(accounts) $ python manage.py startapp accounts
(accounts) $ python manage.py runserver
```

* It's important to wait until after creating new custom user model before run migrate to configuring database.

## Custom User Model

1. update config/settings.py


* In settings.py add the accounts app and use the AUTH_USER_MODEL config to tell Django to use our new custom user model in place of the built-in User model.

* Within INSTALLED_APPS add accounts at the bottom. Then at the bottom of the entire file, add the AUTH_USER_MODEL config.


2. create a new CustomUser model
* update accounts/models.py with a new User model which we'll call CustomUser.
3. create new UserCreation and UserChangeForm
* create a new file in the accounts app called forms.py 

4. update the admin

* after these steps run **makemigrations** and **migrate** for the first time to create a new database that uses the custom user model.

## Superuser
```bash
$ python manage.py createsuperuser
```

## Templates/Views/URLs

1. Start by updating settings.py to use a project-level templates directory.
2. set the redirect links that go to  home template. 
3. Create a new project-level templates folder  and create templates files
4. link the urls.py files at the project and app level.
5. Create a urls.py file in the accounts app.
6. Last step is views.py file in the accounts app which will contain the form 
# DjangoX
A batteries-included Django starter project. For a production-ready version see the book Django for Professionals.