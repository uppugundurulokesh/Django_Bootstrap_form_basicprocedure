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
   
   
   ***registerdata.html***
   
   	<body>
	<div class="container">
	  <h2>Register Form</h2>
	  <form action="{% url 'registerdata' %}" method="POST">
		{% csrf_token %}
	    <div class="form-group">
	      <label for="firstName" class='bg'>firstName:</label>
	      <input type="text" class="form-control" id="firstName" name="firstName" placeholder="Enter First Name" style="width:30%">
	    </div>
	    <div class="form-group">
	      <label for="lastName" class='bg'>lastName:</label>
	      <input type="text" class="form-control" id="lastName" name="lastName" placeholder="Enter Last Name" style="width:30%">
	    </div>

	    <input type="submit" name="submit"value = "SAVE">
	  </form>
	</div>  
	</body>
	
  ***detailpage.html***
  
	<body>
		<h2>This is {{ bio.lastName }} @ welcome </h2>
	</body>
   
   6. ***implement models.py file:***
   > Model is nothing but data. So, a model class’s fields map to database fields, By using this fields columns of table is created in admin database
   
   > In this models.py file we create one class for map to dabase fields. By using this class name table name is created with this fields.
   
    from django.db import models

    # Create your models here.
    class studentdata(models.Model):
	
	firstName=models.CharField(max_length=50)
	lastName=models.CharField(max_length=50)
	
	def __str__(self):
		return self.firstName+" "+self.lastName
		
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
      
9. ***configure the url's***
>To Present the data 'views' which is mapped to url's pattern. Edit the url.py file as follow,

    from django.contrib import admin
    from django.urls import path
    from dbtest import views
    urlpatterns = [
        path('admin/', admin.site.urls),
        path('registerdata/',views.registerdata,name='registerdata'),
    ]
10. ***configure the views.py file***
>After complete the url.py file we have to implemement views.py files. views.py working like a controller for controlling the all the navigations. In url.py file we declare a path for calling the views.regiserdata so, that function should be implemement in views.py file

    from django.shortcuts import render
    from dbtest.models import studentdata

    # Create your views here.
    def registerdata(request):
	if request.method=='POST':
		firstName=request.POST['firstName']
		lastName=request.POST['lastName']

		bio={'firstName':firstName,'lastName':'lastName'}
		obj=studentdata(firstName=firstName,lastName=lastName)
		obj.save()
		return render(request,'practapp/detailpage.html',{'bio':bio})


	return render(request,'practapp/registerdata.html',{})

	
In views.py file we create one function name with registerdata. In this function we post the all html form feilds of data into model classes with dictionary formate and this model class data saved into admin database. Once registerdata saved then it will navigate to detailpage.html otherwise it will navigate to registerdata.html file

11. ***Run the server and test the app***
> Open command prompt the type the follow command:- **python manage.py runserver**. Open Chrome browser then enter the local host path:- https://127.0.0.1:8000/registerdata

> If it working fine, then fill the form and click on save button, and then check it admin database for data saved or not

> Now, check django admin databse is data saved or not, Open https://127.0.0.1:8000/admin  login the database using your superuser credintials.

> If data saved then you done a great job!, Thank you.....!



   
   
   
  
  
            
       
   



 
 
 
 
 
 
 
