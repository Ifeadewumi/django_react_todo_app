# Django + React Todo Notes App

This project was attempted with the intent of understanding how to integrate a React frontend project with a Django backend project.

I used this tutorial: https://www.digitalocean.com/community/tutorials/build-a-to-do-application-using-django-and-react

## Installation Instructions
### Setting up the backend
Create a new project directory:
`mkdir django-todo-react`

Navigate into the directory:
`cd django-todo-react`

Now install pipenv using pip:
`pip install pipenv`

Now, activate a new virtual environment:
`pipenv shell`

Install django using pipenv:
`pipenv install django`

Now, create a new project called `backend`:
`django-admin startproject backend`

Start a new application called `todo` in the newly created backend directory:
`python manage.py startapp todo`

Register and run migrations on the todo app

Run the server.


### Integrating the two sides

To set up the API through which the react and django sides would communicate, you need to install `djangorestframework` and `django-cors-headers` in your virtual environment.

Then, add `rest_framework` and `corsheaders` to your list of installed apps in `backend/settings.py`. Also, add `corsheaders.middleware.CorsMiddleware` to the list of middleware in `backend/settings.py`.

Then, add these lines of code to the bottom of the `backend/settings.py` file:

```
CORS_ORIGIN_WHITELIST = [
    'http://localhost:3000'
]
```

The `django cors headers` package allows us to run both django  and, in this case, node servers by whitelisting the port Node runs on. While python will still run on the 8000 port by default (except otherwise specified), node will still be able to run on the 3000 port.

We will soon link the two together.

### Setting up the Frontend
Open a new terminal window and navigate to the `django-todo-react` project directory.

We will create a react app using `create-react-app`. The exact approach you use will depend on you. rBelow is the approach I used:
`npx create-react-app frontend`

Change into the `frontend` directory:
`cd frontend`.

Next, install `bootstrap` and `reactstrap`.

Next add `bootstrap.min.css` in the `frontend/src/index.js`.

Next install `axios` in the frontend directory.

Next, add the following line to the `frontend/package.json`:

`"proxy": "http://localhost:8000",`

Running your node app now shows you interacting with the database through the django logic.

Note that the two servers have to be live. You can use two different terminal windows.

## Further work

I need help debugging my frontend code. Something is wrong with it but I don't know where to check. The button for 'Complete' is not responding.

Also, let me know if you have any questions.