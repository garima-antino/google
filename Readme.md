In this project ,I am going to show you how to use social authentication in django applications.By this user can login easily with google.
now we have to follow these steps-

1)install the following requirements-
	pip install django
	pip install social-auth-app-django

2) Setup the django project
	
3)Add the following in settings.py

 	in 'Installed_Apps' 
		'social_django',
    		'Your_app_name',
 
	to 'MIDDLEWARE'
		'social_django.middleware.SocialAuthExceptionMiddleware',
	
	in 'TEMPLATES'
		'social_django.context_processors.backends',
	
	AUTHENTICATION_BACKENDS = [
    		'social_core.backends.google.GoogleOAuth2',
    		'django.contrib.auth.backends.ModelBackend',
	]
	LOGIN_URL = 'login'
	LOGIN_REDIRECT_URL = 'home'
	LOGOUT_URL = 'logout'
	LOGOUT_REDIRECT_URL = 'login'
	SOCIAL_AUTH_GOOGLE_OAUTH2_KEY = 'your client id'
	SOCIAL_AUTH_GOOGLE_OAUTH2_SECRET = 'your secret key'

4)Now create the views
	a)in login view return the login page template
	b)after logging in return the home page template by using @login_required decorator

5) Now create the login and home page or where you want to redirect the user after logging in


6) Create the endpoints

7) Now you have to generate the secret key and client id from 'google developer console'
	
	a)Go to google developer console
	b)Create a new project
	c) Click on credentials
	d)Click on “Configure Consent Screen”
	e)Select External. Click on create.
	f)Enter app name: testapp. Add your support email
	g)At the bottom. Add developer contact information. Click on save and continue.
	h)Click on save and continue 2 times. Then click on back to the dashboard.
	i)Again click on credentials.
	j)Click on create credentials. Click on OAuth Client ID.
	h)Select Application type as web.
	i)Add two Authorized Javascript origin URLs: http://localhost:8000 and http://127.0.0.1:8000
	j)Authorized Redirect URIs: http://localhost:8000/social-auth/complete/google-oauth2/
	k)Click on create.

8)Copy and paste the client id and client secret to your settings.py.

9)Run the following commands

	python manage.py makemigrations
	python manage.py migrate
	python manage.py runserver

10) Now you can easily login with google
