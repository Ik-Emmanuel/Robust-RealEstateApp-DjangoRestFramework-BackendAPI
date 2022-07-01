# Robust-RealEstateApp-DjangoRestFramework-BackendAPI
Complete backend  REST API service for a real estate application using 
 - `Django-REST-Framework`
 - `Djoser and JWT`
 -  `PostgreSQL Database`
-----

### Introduction  and Overview
This REST API was built with python's Django RESTFramework. This is a complete production ready backend service for a real-estate like operations. The API exposes property listings data from a PostgresSQL database and it allows users to:
- Sign up and Register on the platform 
- Get registration activation email
- Change password using the "forgot password" feature 
- Specify either user account type as either agent or normal user 
- Upload several media files 
- Search for listings data using `api search` features , `api result pagination` feature etc.  

# Key Project Features:
- Custom user model using AbstractBaseModel 
- User authentication with JWT (access/refresh token)
- User activation link email
- User password change feature (forgot password feature)
- API testing with PyTest
- Media file upload
- Application Logging
- Django Signals

## Versions and Dependencies
- Python 3.9.9
- Django==3.2.7

## Set Up and Run
- Create a virtual enviroment with the python version
- Install dependencies from requirements.txt `pip install requirements.txt`
- Run command: `python manage.py runserver`

## Important Commands
```

 * python manage.py runserver 
 * python manage.py createsuperuser - used to create new admin user 
 * python manage.py makemigrations  - used to make migrations when new models are added 
 * python manage.py migrate - used to run actual migration

 # Pytest 
 * pytest --ignore=env/ --ignore=/env/  -p no:warnings --cov=.

```
> **Note**  Configure an `.env` file to enter enviroemnt variable as seen in  `.env.example`. 
> enter all needed env variables
> create a `mailtrap` account to test email sending or configure email settings 
## Available API Endpoints
| METHOD | ROUTE | FUNCTIONALITY |ACCESS|
| ------- | ----- | ------------- | ------------- |
| *POST* | ```/api/v1/auth/users/``` | _Register new user_| _All users_|
| *POST* | ```/api/v1/auth/users/reset_password/``` | _User password reset request_| _All users_|
| *POST* | ```/api/v1/auth/users/reset_password_confirm/``` | _User password reset confirmation_| _All users_|
| *POST* | ```/api/v1/auth/jwt/create/``` | _User login and token generation_| _All users_|
| *POST* | ```/api/v1/auth/users/activation/``` | _User new account activation_| _All users_|
| *POST* | ```/api/v1/ratings/<agent_uuid>/``` | _Agent ratings_|  _Authenticated users only_|
| *GET* | ```/api/v1/properties/all/``` | _Get all properties_| _All users_|
| *GET* | ```/api/v1/properties/all/?price__lt=177845``` | _Filter properties_| _All users_|
| *GET* | ```/api/v1/properties/details/<property-slug>``` | _View Property details_| _All users_|
| *GET* | ```/api/v1/properties/agents/``` | _View Properties of signed in agent_| _Authenticated agent only_|
| *POST* | ```/api/v1/properties/create/``` | _Create a new property_| _Authenticated agent only_|
| *DELETE* | ```/api/v1/properties/delete/prperty-to-be-deleted3/``` | _Delete a property_| _Authenticated agent only_|
| *GET* | ```/api/v1/profile/agents/all/``` | _Get all agents_| _All users_|
| *GET* | ```/api/v1/profile/top-agents/all/``` | _Get top rated agents_| _All users_|
| *PUT* | ```/api/v1/properties/update/<property-slug>``` | _Updatea given property_| _Authenticated agent only_|
| *PATCH* | ```/api/v1/profile/update/<agent-username>/``` | _Updatea given user profile_| _Authenticated users only_|
| *GET* | ```/api/v1/profile/me``` | _Get Signed in users profile_| _Authenticated users only_|
| *POST* | ```/api/v1/enquiries/``` | _Send user enquiry email_|  _Authenticated users only_|

