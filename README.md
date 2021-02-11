# Boutique E-Commerce Website
[Boutique Ado](https://randyaajr-shop.herokuapp.com/)

If you’re looking for something new, you’re in the right place. We strive to be industrious and innovative, offering our customers something 
they want, putting their desires at the top of our priority list. We believe everyone should live in a home they love. Whether you are 
furnishing a room in your home, designing an office space or remaking a commercial environment for a hospitality or restaurant location, 
we understand a well-designed project is defined by balance.

The interests of our customers are always top priority for us, so we hope you will enjoy our products as much as we enjoy making them 
available to you.

## Table of Contents
1. [**UX**](#ux)
    - [**Project Goals**](#project-goals)
    - [**User Stories**](#user-stories)
    - [**Design**](#design)

2. [**Features**](#features)
    - [**Store Features**](#store-features)
3. [**Information Architecture**](#information-architecture)
    - [**Database Choice**](#database-choice)
    - [**Data Modelling**](#data-modelling)

4. [**Technologies Used**](#technologies-used)
    - [**Languages**](#languages)
    - [**Libraries and Frameworks**](#libraries-and-frameworks)
    - [**Tools**](#tools)
    - [**Databases**](#databases)

5. [**Deployment**](#deployment)
    - [**Local Deployment**](#local-deployment)
    - [**Heroku Deployment**](#heroku-deployment)
    

## UX

### Project Goals
#### Target Audience
- Individuals under lockdown restrictions that need clothing or homeware
- Individuals who enjoy shopping online
- Individuals who want to get a new experience, curious about what other e-commerce stores have to offer
- People interested in fassion  

#### Business goals(site owner's goals):
- Provide users with a secure professional e-commerce online shop
- Make profit from selling clothing, bed&bath and kitchen products
- Grow on an country wide scale
- Make the brand more recognisable and expand the business
### User Stories    
#### Common user stories (guests, new users and authenticated users)
- As a user, I expect to access the website from any device, so that I can use the website anytime and anywhere.
- As a user, I expect to easily navigate the website, so that I can quickly find what I'm looking for.
- As a user, I want to easily access social media links of the company, so that I can read more information about it.
- As a user, I want to be able to easily contact the owner/manager of the company, so that I can write an additional query or ask a question.
- As a user, I want to view service details and product details (e.g. image, price, description), so that I can buy some of them.
- As a user, I want to search and filter the products easily, so that I can quickly find a specific product I am looking for.
- As a user, I want to view and modify my order in the cart before completing it, so that I can make last changes easily before proceeding to payment. 
- As a user, I want to view a total price of my purchases and delivery cost, so that I will understand and see how much I will be charged.
- As a user, I expect to make payments by card in a safe and secure way, so that I won't be concerned about the safety of my card details and won't be charged incorrectly.
- As a user, I want to receive an email confirmation after checkout, so that I can make sure that payment was successfull.
#### New Users
- As a user, I want to create my own account, so that I can save, view and edit my profile and delivery details and view my order history.
#### Returning users
- As a user, I want to easily login anytime, so that I can get access to my saved profile details and make next purchase quicker.
- As a user, I want to reset my password if I forgot it, so that I can get access to my profile again. 
- As a user, I want to  be able to change my password, so that I can create the stronger password (e.g.in case I published my old password somewhere) to protect my personal details.    
- As a user, I want to  be able to change my email or add the second email, so that I can have an easier access to the website's functionality and to gain more flexibility.
#### Website Owner(admin)
- As a user, I want to have convenient and secure admin interface avalable only for website admin, so that I can add, edit and remove products/services.
- As a user, I want to receive emails from the users when they fill out the contact form, so that I can reply on them satisfying users queries.
### Design
#### Framework
- [Bootstrap](https://www.bootstrapcdn.com/), front-end framework is chosen for this project for its modern interface, ease of use and ability to be easily customized. It is used for creating features such as navbar, cards, forms, modals, as well as for the layout.
- [JQuery](https://jquery.com/) is used for initializing some Bootstrap components, as well as for custom functions.


#### Icons
Icons are used widely, as they are good attention grabbers. They help users to find and scan content quickly and easily. Another advantage of using them is to help to break language barriers. They create more user-friendly experience for people with non-native English by giving the visual clue about the subject.   
- I used [FontAwesome](https://fontawesome.com/) as the main icon library across the project (e.g. for social media links, forms, cart, search and user icons in navigation).

<div align="right">
    <b><a href="#table-of-contents">↥ Back To Top</a></b>
</div>

## Features

### Store Features
- Product search
- Product filter functionality
- Fully functional payment system
- Full-featured authentication system including email confirmations and user profiles
- Real-time notifications that guide the user's experience

<div align="right">
    <b><a href="#table-of-contents">↥ Back To Top</a></b>
</div>

---

## Information Architecture
### Database choice
During the development phase I worked with **sqlite3** database which is installed with Django.   
For deployment(production), a **PostgreSQL** database is provided by Heroku as an add-on.
- The **User model** used in this project is provided by Django as a part of defaults `django.contrib.auth.models`. More information about Django’s authentication system can be found [here](https://docs.djangoproject.com/en/3.0/ref/contrib/auth/).

### Data Modelling
#### Profile App
##### Profile
| **Name** | **Database Key** | **Field Type** | **Validation** |
--- | --- | --- | --- 
 User | user | OneToOneField 'User' |  on_delete=models.CASCADE
 Phone number | default_phone_number | CharField | max_length=20, null=True, blank=True
 Address Line1 | default_street_address1 | CharField | max_length=60, null=True, blank=True
 Address Line2 | default_street_address2 | CharField | max_length=60, null=True, blank=True
 Town/City | default_town_or_city | CharField | max_length=50, null=True, blank=True
 County | default_county | CharField | max_length=50, null=True, blank=True
 Postcode | default_postcode | CharField | max_length=20, null=True, blank=True
 Country | default_country | CountryField | blank_label='Country', null=True, blank=True

#### Products App
##### Product
| **Name** | **Database Key** | **Field Type** | **Validation** |
--- | --- | --- | --- 
 Category | category | ForeignKey 'Category' | null=True, blank=True, on_delete=models.SET_NULL
 Sku | sku | models.CharField | max_length=254, null=True, blank=True 
 Name | name | models.CharField | max_length=254 
 Description | description | models.TextField |
 Rating | rating | models.DecimalField | max_digits=6, decimal_places=2, null=True, blank=True
 Has sizes | has_sizes | models.BooleanField | default=False, null=True, blank=True
 Price | price | models.DecimalField | max_digits=6, decimal_places=2
 Rating | rating | models.DecimalField | max_digits=6, decimal_places=2, null=True, blank=True
 Image Url | image_url | models.URLField | max_length=1024, null=True, blank=True
 Image | image | models.ImageField | null=True, blank=True

##### Category
| **Name** | **Database Key** | **Field Type** | **Validation** |
--- | --- | --- | --- 
Programmatic Name | name | CharField | max_length=254
Friendly Name | friendly_name | CharField | max_length=254, null=True, blank=True

<div align="right">
    <b><a href="#table-of-contents">↥ Back To Top</a></b>
</div>

---

## Technologies Used

### Languages
- [HTML](https://developer.mozilla.org/en-US/docs/Web/HTML)
- [CSS](https://developer.mozilla.org/en-US/docs/Web/CSS) 
- [JavaScript](https://www.javascript.com/)
- [Python](https://www.python.org/) 
- [Jinja](https://jinja.palletsprojects.com/en/2.10.x/) - templating language for Python, to display back-end data in HTML.

### Libraries and Frameworks
- [Django](https://www.djangoproject.com/) - Python framework for building the project.
- [Bootstrap](https://www.bootstrapcdn.com/) - as the front-end framework for layout and design.
- [FontAwesome](https://fontawesome.com/) - to provide icons used across the project. 
- [JQuery](https://jquery.com/) - to simplify DOM manipulation and to initialize Bootstrap functions.
- [Gunicorn](https://pypi.org/project/gunicorn/) - a Python WSGI HTTP Server to enable deployment to Heroku.
- [Psycopg2](https://pypi.org/project/psycopg2/) - to enable the PostgreSQL database to function with Django.
- [Stripe](https://stripe.com/ie) - to handle financial transactions.
- [Django Crispy Forms](https://django-crispy-forms.readthedocs.io/en/latest/) - to style Django forms.

### Tools
- [GitPod](https://www.gitpod.io/) - an online IDE for developing this project.
- [Git](https://git-scm.com/) - for version control.
- [GitHub](https://git-scm.com/) - for remotely storing project's code.
- [PIP](https://pip.pypa.io/en/stable/installing/) - for installation of necessary tools.
- [Heroku](https://heroku.com/) - to host the project.
- [AWS S3 Bucket](https://aws.amazon.com/) -  to store static and media files in prodcution.
- [Boto3](https://boto3.amazonaws.com/v1/documentation/api/latest/index.html) for compatibility with AWS.
- [Travis](https://travis-ci.org/) - for integration testing.
- [Balsamiq](https://balsamiq.com/) - to create wireframes.

### Databases
- [SQlite3](https://www.sqlite.org/index.html) - a development database.
- [PostgreSQL](https://www.postgresql.org/) - a production database.

<div align="right">
    <b><a href="#table-of-contents">↥ Back To Top</a></b>
</div>

---

## Deployment
Boutique Ado was developed using the [GitPod](https://www.gitpod.io/) online IDE and
using Git & GitHub for version control. It is hosted on the [Heroku](https://heroku.com/) platform, with static and images files being hosted in AWS S3 Basket.

### Local Deployment
To be able to run this project, the following tools have to be installed:
- An IDE of your choice ([GitPod](https://www.gitpod.io/) was utilized for creating Boutique Ado)
- [Git](https://git-scm.com/)
- [PIP](https://pip.pypa.io/en/stable/installing/) 
- [Python3](https://www.python.org/download/releases/3.0/)    

Apart from that, you also need to create accounts with the following services:
- [Stripe](https://stripe.com/en-ie)
- [AWS](https://aws.amazon.com/) to setup the [S3 basket](https://docs.aws.amazon.com/AmazonS3/latest/gsg/CreatingABucket.html)
- [Gmail](https://mail.google.com/)

#### Directions
1. You can clone this repository directly into the editor of your choice by pasting the following command into the terminal:   
`git clone https://github.com/irinatu17/Art-of-Tea`    
Alternatively, you can save a copy of this repository by clicking the green button **Clone or download** , then **Download Zip** button, and after extract the Zip file to your folder.      
In the terminal window of your local IDE change the directory (CD) to the correct file location (directory that you have just created).       

Note: You can read more information about the cloning process on the [GitHub Help page](https://docs.github.com/en/github/creating-cloning-and-archiving-repositories/cloning-a-repository).   

2. Set up environment variables (.env file does not need to be created using gitpod).     
Note, that this process will be different depending on IDE you use.   
In this it was done using the following way:      
    - Create `.env` file in the root directory.
    - Add `.env` to the `.gitignore` file in your project's root directory
    - In `.env` file set environment variables with the following syntax:     
    ```bash 
    import os  
    os.environ["DEVELOPMENT"] = "True"    
    os.environ["SECRET_KEY"] = "<Your Secret key>"    
    os.environ["STRIPE_PUBLIC_KEY"] = "<Your Stripe Public key>"    
    os.environ["STRIPE_SECRET_KEY"] = "<Your Stripe Secret key>"    
    os.environ["STRIPE_WH_SECRET"] = "<Your Stripe WH_Secret key>"    
    os.environ["GOOGLE_MAP_KEY"] = "<Your Google Map key>" 
     ```
       
Read more about how to set up the Stripe keys in the [Stripe Documentation](https://stripe.com/docs/keys)
    
3. Install all requirements from the **requirements.txt** file putting this command into your terminal:     
`pip3 install -r requirements.txt`     
4. In the terminal in your IDE migrate the models to crete a database using the following commands:    
`python3 manage.py makemigrations`     
`python3 manage.py migrate`     
5. Load the data fixtures(**categories**, **products**, **itinerary**, **itinerary_items**, **events**) in that order into the database using the following command:    
`python3 manage.py loaddata <fixture_name>`        
6. Create a superuser to have an access to the the admin panel(you need to follow the instructions then and insert username,email and password):    
`python3 manage.py createsuperuser`   
7. You will now be able to run the application using the following command:     
`python3 manage.py runserver`     
8. To access the admin panel, you can add the `/admin` path at the end of the url link and login using your superuser credentials.

### Heroku Deployment
*To start Heroku Deployment process, you need to clone the project as described in the [Local deployment](#local-deployment) section above.*     
To deploy the project to [Heroku](https://heroku.com/) the following steps need to be completed:    
1. Create a **requirement.txt** file, which contains a list of the dependencies, using the following command in the terminal:    
`pip3 freeze > requirements.txt`    
2. Create a **Procfile**, in order to tell Heroku how to run the project, using the following command in the terminal:      
`web: gunicorn art_of_tea.wsgi:application`    
3. `git add`, `git commit` and `git push` these files to GitHub repository.     
NOTE: these 1-3 steps already done in this project and included in the GitHub repository, but illistrated here as they are required for the successfull deployment to Heroku.        
As well as that, other things that are required for the Heroku deployment and have to be installed: **gunicorn** (WSGI HTTP Server), **dj-database-url** for database connection and **Psycopg** (PostgreSQL driver for Python). All of the mentioned above are *already installed* in this project in the requirements.txt file.     
4. On the [Heroku](https://heroku.com/) website you need to create a **new app**, assigne a name (must be unique),set a region to the closest to you(for my project I set Europe) and click **Create app**.   
5. Go to **Resources** tab in Heroku, then in the **Add-ons** search bar look for **Heorku Postgres**(you can type `postgres`), select **Hobby Dev — Free** and click **Provision** button to add it to your project.     
6. In Heroku **Settings** click on **Reveal Config Vars**.   
7. Set the following config variables there:     

| KEY            | VALUE         |
|----------------|---------------|
| AWS_ACCESS_KEY_ID | `<your aws access key>`  |
| AWS_SECRET_ACCESS_KEY | `<your aws secret access key>`  |
| DATABASE_URL| `<your postgres database url>`  |
| EMAIL_HOST_PASS | `<your email password(generated by Gmail)>` |
| EMAIL_HOST_USER| `<your email address>`  |
| GOOGLE_MAP_KEY| `<your google map key>`  |
| SECRET_KEY | `<your secret key>`  |
| STRIPE_PUBLIC_KEY| `<your stripe public key>`  |
| STRIPE_SECRET_KEY| `<your stripe secret key>`  |
| STRIPE_WH_SECRET| `<your stripe wh key>`  |
| USE_AWS | `True`  |
     
8. Copy **DATABASE_URL's value**(Postrgres database URL) from the Convig Vars and temporary paste it into the default database in **settings.py**.     
You can temporary comment out the current database settings code and just paste the following in the settings.py:   
```bash 
  DATABASES = {     
        'default': dj_database_url.parse("<your Postrgres database URL here>")     
    }
  ```
Important Note: that's just temporary set up, this URL **should not be committed and published to GitHub** for security reasons, so make sure not to commit your changes to Git while the URL is in the settings.py.   
  
9. Migrate the database models to the Postgres database using the following commands in the terminal:    
    `python3 manage.py makemigrations`     
    `python3 manage.py migrate`     
10. Load the data fixtures(**categories**, **products**, **itinerary**, **itinerary_items**, **events**) into the  Postgres database using the following command:     
    `python3 manage.py loaddata <fixture_name>`      
11. Create a **superuser** for the Postgres database by running the following command(*you need to follow the instructions and inserting username,email and password*):      
`python3 manage.py createsuperuser`     
12. You need to remove your Postgres URL database from the settings and uncomment the default DATABASE settings code in the settings.py file.    
Note: for production you get the environment variable 'DATABASE_URL' from the Heroku Config Vars and use Postgress database, while for development you use the SQLite as a default database.     
13. Add your Heroku app URL to **ALLOWED_HOSTS** in the settings.py file.
14. You can connect Heroku to GitHub to automatically deploy each time you push to GitHub.    
To do so, from the Heroku dashboard follow the steps:
-  **Deploy** section -> **Deployment method** -> select **GitHub**
-  link the Heroku app to your GitHub repository for this project
- click **Enable Automatic Deploys** in the Automatic Deployment section
- Run `git push` command in the terminal, that would now push your code to both Github and Heroku, and perform the deployment.     

Alternatively, in the terminal you can run:    
- `heroku login`    
-  after adding and comitting to Git, run the following command:     
`git push heroku master`
15. After successful deployment, you can view your app bu clicking **Open App** on Heroku platform.
16. You will also need to verify your email address, so you need to login with your superuser credentials and verify your email address in the admin panel. Now you will be able to view the app running!    
##### Hosting media files with AWS
The **static files** and **media files** (that will be uploaded by superuser - product/service images) are hosted in the [AWS S3 Bucket](https://aws.amazon.com/). To host them, you need to create an account in AWS and create your S3 basket with *public access*. More about setting it up you can read in [Amazon S3 documentation](https://docs.aws.amazon.com/AmazonS3/latest/gsg/CreatingABucket.html) and [this tutorial](https://django-storages.readthedocs.io/en/latest/backends/amazon-S3.html).
##### Senging email via Gmail
In order to send real emails from the application, you need to connect it to your **Gmail account**, setting up your **email address** in EMAIL_HOST_USER variable and your **app password** generated by your email provider in EMAIL_HOST_PASS variable.

<div align="right">
    <b><a href="#table-of-contents">↥ Back To Top</a></b>
</div>

---
