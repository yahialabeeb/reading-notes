# JSON Web Token 
## What is JSON Web Token
It defines a compact and self-contained way for securely transmitting information between parties as a JSON object. 

## where it usful?
1. Authorization

2. Information Exchange

## What is the JSON Web Token structure?
a JWT typically looks like the following.
Header.payload.Signature

JSON Web Tokens consist of three parts:

### 1. Header

The header typically consists of two parts: the type of the token, which is JWT, and the signing algorithm being used, such as HMAC SHA256 or RSA.

### 2. payload
payload contains the claims.
Claims are statements about an entity and additional data. 
### types of claims:

1. Registered claims: These are a set of predefined claims which are not mandatory but recommended, to provide a set of useful, interoperable claims. Some of them are: iss (issuer), exp (expiration time), sub (subject), aud (audience), and others.

2. Public claims: These can be defined at will by those using JWTs. But to avoid collisions they should be defined in the IANA JSON Web Token Registry or be defined as a URI that contains a collision resistant namespace.

3. Private claims: These are the custom claims created to share information between parties that agree on using them and are neither registered or public claims.

### 3. Signature
To create the signature part you have to take the encoded header, the encoded payload, a secret, the algorithm specified in the header, and sign that.

The signature is used to verify the message wasn't changed along the way, and, in the case of tokens signed with a private key, it can also verify that the sender of the JWT is who it says it is.

Putting all together
The output is three Base64-URL strings separated by dots that can be easily passed in HTML and HTTP environments, while being more compact when compared to XML-based standards such as SAML.


## How do JSON Web Tokens work?
In authentication, when the user successfully logs in using their credentials, a JSON Web Token will be returned. Since tokens are credentials, great care must be taken to prevent security issues. In general, you should not keep tokens longer than required.

![i](401reads/client-credentials-grant.png)
1. The application or client requests authorization to the authorization server. This is performed through one of the different authorization flows. For example, a typical OpenID Connect compliant web application will go through the /oauth/authorize endpoint using the authorization code flow.
2. When the authorization is granted, the authorization server returns an access token to the application.
3. The application uses the access token to access a protected resource (like an API).


## How JWT Works?
The JWT is just an authorization token that should be included in all requests:
```bash
curl http://127.0.0.1:8000/hello/ -H 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoiYWNjZXNzIiwiZXhwIjoxNTQzODI4NDMxLCJqdGkiOiI3ZjU5OTdiNzE1MGQ0NjU3OWRjMmI0OTE2NzA5N2U3YiIsInVzZXJfaWQiOjF9.Ju70kdcaHKn1Qaz8H42zrOYk0Jx9kIckTn9Xx7vhikY'
```
* The JWT is acquired by exchanging an username + password for an access token and an refresh token.

* The access token is usually short-lived (expires in 5 min or so, can be customized though).

* The refresh token lives a little bit longer (expires in 24 hours, also customizable). It is comparable to an authentication session. After it expires, you need a full login with username + password again

## Installation & Setup
1. In terminal 
```bash
pip install djangorestframework_simplejwt
```
2.In settings.py
```python 
REST_FRAMEWORK = {
    'DEFAULT_AUTHENTICATION_CLASSES': [
        'rest_framework_simplejwt.authentication.JWTAuthentication',
    ],
}
```
3. In urls.py
```python 
from django.urls import path
from rest_framework_simplejwt import views as jwt_views

urlpatterns = [
    # Your URLs...
    path('api/token/', jwt_views.TokenObtainPairView.as_view(), name='token_obtain_pair'),
    path('api/token/refresh/', jwt_views.TokenRefreshView.as_view(), name='token_refresh'),
]
``` 

## Usage

1. Obtain Token
First step is to authenticate and obtain the token. The endpoint is /api/token/ and it only accepts POST requests.
```bash
http post http://127.0.0.1:8000/api/token/ username=vitor password=123
``` 

So basically your response body is the two tokens:
```bash
{
    "access": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoiYWNjZXNzIiwiZXhwIjoxNTQ1MjI0MjU5LCJqdGkiOiIyYmQ1NjI3MmIzYjI0YjNmOGI1MjJlNThjMzdjMTdlMSIsInVzZXJfaWQiOjF9.D92tTuVi_YcNkJtiLGHtcn6tBcxLCBxz9FKD3qzhUg8",
    "refresh": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoicmVmcmVzaCIsImV4cCI6MTU0NTMxMDM1OSwianRpIjoiMjk2ZDc1ZDA3Nzc2NDE0ZjkxYjhiOTY4MzI4NGRmOTUiLCJ1c2VyX2lkIjoxfQ.rA-mnGRg71NEW_ga0sJoaMODS5ABjE5HnxJDb0F8xAo"
}
``` 

2. After that you are going to store both the access token and the refresh token on the client side, usually in the localStorage.


3. Refresh Token
To get a new access token, you should use the refresh token endpoint /api/token/refresh/ posting the refresh token:
```bash 
http post http://127.0.0.1:8000/api/token/refresh/ refresh=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoicmVmcmVzaCIsImV4cCI6MTU0NTMwODIyMiwianRpIjoiNzAyOGFlNjc0ZTdjNDZlMDlmMzUwYjg3MjU1NGUxODQiLCJ1c2VyX2lkIjoxfQ.Md8AO3dDrQBvWYWeZsd_A1J39z6b6HEwWIUZ7ilOiPE
``` 
* The return is a new access token that you should use in the subsequent requests.

* The refresh token is valid for the next 24 hours. When it finally expires too, the user will need to perform a full authentication again using their username and password to get a new set of access token + refresh token.

## What’s The Point of The Refresh Token?
1. It is necessary to make sure the user still have the correct permissions. If your access token have a long expire time

2. A security aspect, in a sense that the refresh token only travel in the POST data. And the access token is sent via HTTP header, which may be logged along the way. So this also give a short window, should your access token be compromised.


# Django Runserver Is Not Your Production Server



### DO NOT USE THIS SERVER IN A PRODUCTION SETTING. It has not gone through security audits or performance tests.

* The server started with runserver is not guaranteed to be performant (it’s very slow), and it hasn’t been built with security concerns in mind. Not a good fit for production use.


## A Production Stack
* It's the right way to approach this
* You want to only use tech in production, which is reliable, well tested and has been around for a while.

* A production setup usually consists of multiple components, They are fast, reliable and very focused.

* When a request arrives at your server, it should be passed to a dedicated web server. 
* Nginx is an example for a good web server.

* The next component is an application server. It gets those fancy requests and uses them to construct Python objects which are usable by Django. WSGI is a specification which people agreed on, which describe how that happens. Gunicorn is an example for a WSGI server.

## How Does Django Fit In?
The project provides a uwsgi.py file, which contains a function to be called by the application server. This function gets a Python object representing the incoming request.

This function calls your code, and produces a response object which is passed to the WSGI server. There the response is translated into a HTTP response and is passed back to the web server, which finally delivers it to the user.

## In Conclusion
* If you want to run Django in production, be sure to use a production-ready web server like Nginx, and let your app be handled by a WSGI application server like Gunicorn.

* If you plan on running on Heroku, a web server is provided implicitly. You don’t have to take care of it. You just need to specify a command to run your application server 