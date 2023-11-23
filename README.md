# Ex-04-Django-Models

#Name: guntur shaik mohammad shahil 

#Reference no: 23011002

# AIM:
To create a django models.

# PROCEDURE:
## Step 1:
Create django project and app using the following commands:

django-admin startproject mymodels

python manage.py startapp myapp

## Step 2:
Create a user_profile models in model.py.

```python
from django.db import models
from django.contrib.auth.models import User

class UserProfile(models.Model):
    user = models.OneToOneField(User, on_delete=models.CASCADE)
    first_name = models.CharField(max_length=100)
    last_name = models.CharField(max_length=100)
    email = models.EmailField()
    
```
## Step 3:
Add the models in the admin interface using the code in admin.py

```python 
from django.contrib import admin
from .models import UserProfile

admin.site.register(UserProfile)

```
## Step 4:
Write the function based view to render the data from the models to the template in view.py.

```python
from django.shortcuts import render
from django.contrib.auth.decorators import login_required
from .models import UserProfile

@login_required
def user_profile(request):
    user = request.user
    user_profile, created = UserProfile.objects.get_or_create(user=user)

    context = {
        "user": user,
        "user_profile": user_profile,
        'firstname': user_profile.user.first_name,  # Access first name through the related User model
        "lastname": user_profile.user.last_name,  # Access last name through the related User model
    }
    return render(request, 'myapp/user_profiles.html', context)

```
## Step 5:
Setup the url path for the templates using urls.py.
```python
from django.contrib import admin
from django.urls import path
from myapp import views
from myapp.views import user_profile

urlpatterns = [
    path("admin/", admin.site.urls),
    path('profile/', views.user_profile, name='user_profile'),
]


```
## Step 6:
In settings.py file add the app created. Now do the migrations process to initiate and save the models

python mange.py makemigrations python manage.py migrate

## Step 7:
Create a template as user_profiles.html

```python

<!DOCTYPE html>
<html>
<head>
    <title>User Profile</title>
</head>
<body>
    <h1>User Profile</h1>
    <p><strong>Username:</strong> {{ user.username }}</p>
    <p><strong>First name:</strong> {{ firstname }}</p>
    <p><strong>Last name:</strong> {{ lastname }}</p>
    <p><strong>Email :</strong> {{ user.email }}</p>
    <p><strong>Custom Profile Data:</strong> {{ user_profile.custom_field }}</p>
</body>
</html>
```
## Step 8:
Run the program using the command

python manage.py runserver 8000

In the admin/ page you can view the models created And in the user_profile template page you can see the profile page of the user.

# OUTPUT:
# Ex-04-Django-Models

#Name: SUNIL KUMAR T

#Reference no: 23001650

# AIM:
To create a django models.

# PROCEDURE:
## Step 1:
Create django project and app using the following commands:

django-admin startproject mymodels

python manage.py startapp myapp

## Step 2:
Create a user_profile models in model.py.

```python
from django.db import models
from django.contrib.auth.models import User

class UserProfile(models.Model):
    user = models.OneToOneField(User, on_delete=models.CASCADE)
    first_name = models.CharField(max_length=100)
    last_name = models.CharField(max_length=100)
    email = models.EmailField()
    
```
## Step 3:
Add the models in the admin interface using the code in admin.py

```python 
from django.contrib import admin
from .models import UserProfile

admin.site.register(UserProfile)

```
## Step 4:
Write the function based view to render the data from the models to the template in view.py.

```python
from django.shortcuts import render
from django.contrib.auth.decorators import login_required
from .models import UserProfile

@login_required
def user_profile(request):
    user = request.user
    user_profile, created = UserProfile.objects.get_or_create(user=user)

    context = {
        "user": user,
        "user_profile": user_profile,
        'firstname': user_profile.user.first_name,  # Access first name through the related User model
        "lastname": user_profile.user.last_name,  # Access last name through the related User model
    }
    return render(request, 'myapp/user_profiles.html', context)

```
## Step 5:
Setup the url path for the templates using urls.py.
```python
from django.contrib import admin
from django.urls import path
from myapp import views
from myapp.views import user_profile

urlpatterns = [
    path("admin/", admin.site.urls),
    path('profile/', views.user_profile, name='user_profile'),
]


```
## Step 6:
In settings.py file add the app created. Now do the migrations process to initiate and save the models

python mange.py makemigrations python manage.py migrate

## Step 7:
Create a template as user_profiles.html

```python

<!DOCTYPE html>
<html>
<head>
    <title>User Profile</title>
</head>
<body>
    <h1>User Profile</h1>
    <p><strong>Username:</strong> {{ user.username }}</p>
    <p><strong>First name:</strong> {{ firstname }}</p>
    <p><strong>Last name:</strong> {{ lastname }}</p>
    <p><strong>Email :</strong> {{ user.email }}</p>
    <p><strong>Custom Profile Data:</strong> {{ user_profile.custom_field }}</p>
</body>
</html>
```
## Step 8:
Run the program using the command

python manage.py runserver 8000

In the admin/ page you can view the models created And in the user_profile template page you can see the profile page of the user.

# OUTPUT:
![Screenshot 2023-11-23 092554](https://github.com/mohammadshahil09/ODD2023-WT-Ex-04-Django-Models/assets/145742840/99548df6-e868-46e9-aa4d-156383f2c094)

![Screenshot 2023-11-23 092607](https://github.com/mohammadshahil09/ODD2023-WT-Ex-04-Django-Models/assets/145742840/9a2a8f9d-b0cd-40e6-b4be-94ec1f35f6d0)
