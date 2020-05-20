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
       
   



 
 
 
 
 
 
 
