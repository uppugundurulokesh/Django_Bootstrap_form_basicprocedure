# Django_Bootstrap_form_basicprocedure
Django Bootstrap Form Basic Procedure

# Content:
* Bootstrap
* Bootstrap Integration in Django
* Bootstrap Form Handling with Basic Procedure

### What is Bootstrap?
It is the most popular HTML, CSS, and JavaScript framework for developing responsive, mobile-first websites. Bootstrap 4 is the newest version of Bootstrap, Bootstrap is a free front-end framework for faster and easier web development

***What is Responsive Web Design?*** Responsive web design is about creating web sites which automatically adjust themselves to look good on all devices, from small phones to large desktops.

### How to include bootstrap into our Django Html File?
We can add in three ways

- online: just copay and past bootstrapy style links in header tag

- offline: download the css,jquery,js files from getbootstrap.com and place your downloaded files into respective folder then give the reference link in html header tag

- Django Crispy forms

***Online***

    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.4.1/css/bootstrap.min.css">
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/css/bootstrap.min.css">
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.16.0/umd/popper.min.js"></script>
    <script src="https://maxcdn.bootstrapcdn.com/bootstrap/4.4.1/js/bootstrap.min.js"></script>
    
    //** Just copy and paste this links into your html header tag **//

***Offline***

    1.Download css,jquary,js files from getbootstrap.com
    2.Create static folder in your app folder 
    3.Paste downloading files in static folder
    4.Give the reference link of folder in html header tag
   
 ### Bootstrap Form Handling with basic procedure:
 
 1. Create a new project:
 
        django-admin startproject projectName
        
 2. Create a app in your project:
 
        python manage.py startapp app_name
        
        //** my app name is dbtest **//
        
  3. Run the Server:
  
	     python manage.py runserver
	     
  4. Add your app into installed app(project->settings):
  
    INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'your app name here' 
    ]
    
  5. ***create html forms(registerdata.html and detailpage.html)***
            
   > Now, your all html files should be placed in templates folder. so, create a templates folder in your app folder and then                  create a another folder with your appname under templates folder.
   
   > Place all the html files in this created app folder under templates folder
   
   > If you want to integrate boostrap for your html web page then place online or offline bootstrap style links in html header tag.
   
   ![templates image ](https://github.com/uppugundurulokesh/Django_Bootstrap_form_basicprocedure/blob/master/templates.PNG)
   
   
   6. ***implement models.py file:***
   > Model is nothing but data. So, a model class’s fields map to database fields, By using this fields columns of table is created in admin database
   
   > In this models.py file we create one class for map to dabase fields. By using this class name table name is created with this fields.
   
    from django.db import models

    # Create your models here.
    class studentdata(models.Model):
	firstName = models.CharField(max_length=50)
	lastName = models.CharField(max_length=40)
	userName = models.CharField(max_length=40)
	password = models.CharField(max_length=40)
	mailId = models.CharField(max_length=40)
	phone = models.IntegerField(max_length=40)
	age = models.IntegerField(max_length=40)

	def __str__(self):
		return self.lastName+' '+self.firstName+' '+self.userName+' '+self.mailId+' '+str(self.phone)+' '+str(self.age)
		
7. ***Register a Model class in Django Admin: ***
> created model class should be registered in django admin. so, we have to implement admin.py file as below,

    from django.contrib import admin
    from dbtest.models import studentdata # import model class from your app


    # Register your models here.
    admin.site.register(studentdata)
    
8. ***Sync with admin Database***
> Now, we have to sync the created model class with admin database using makemigrations and migrate, using below commands in command prompt

* Makemigrations: It is used to create a migration file that contains code for the tabled schema of a model
         
      python manage.py makemigrations

* Migrate: It creates table according to the schema defined in the migration file.
		
      python manage.py migrate


   
   
   
  
  
            
       
   



 
 
 
 
 
 
 
