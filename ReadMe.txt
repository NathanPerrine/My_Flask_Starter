Copying this repository (and following a few steps) should give you a starter flask application with a working user_login
To remove the user section, delete the auth blueprint, and any references to the login / sign up pages


Step 0: Tutorial
---- https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-i-hello-world
---- https://elemental-flat-e5b.notion.site/The-Ultimate-Flask-Tutorial-111c0b0b64d9449a8e4aefea44d60a66

Step 1: Create a python virtual environment
---- python -m venv {venv_name}

Step 2: Activate Venv 
---- <name-of-environment>\Scripts\activate
---- If you're getting an error "flask not found" you're using the wrong python interpreter
---- set python interpreter to the new venv
    ---- ctrl + shift + P 
        ---- Python: Select interpreter
        ---- Select the newly created venv

Step 3: Requirements
---- upgrade pip
    ---- python -m pip install --upgrade pip
---- pip install -r requirements.txt
    ---- set version requirements if needed
    ---- 

Step 4: .gitignore
----Update your gitignore file to not track:
    ---- {venv_name}/ <---- Change name to your venv name
    ---- __pycache__/
    ---- .env
    ---- app.db

Step 5: .env 
---- Create a file called '.env' in the top level folder
---- FLASK_APP=run.py
     FLASK_ENV=development
     SECRET_KEY=
     ---- In the terminal enter 'python'
          import os 
          os.urandom(24)
          copy new secret_key
     DATABASE_URL={link to database}
    ---- https://www.elephantsql.com/
    ---- Make sure url starts with "postgresql"

Step 6: templates / base.html
---- Edit Title 
---- Edit Nav Bar 
    ---- Currently is set to bootstrap navbar - light, bottom border, collapses on small screens 
    ---- Separates the sign up / login / logout to the right of the page
    ---- Has several jinja is authenticated checks to change the navbar options




Step x: Blueprints
---- app/__init__.py
    ---- For each blueprint add the following below 'app = flask' before from app import routes
    ---- from app.blueprints.XXXXX import XXXXX
         app.register_blueprint(XXXXX)



Step x: Cloudinary 
---- If you want to store pictures online, upload the images to cloudinary then link the URL generated
---- Sign up for Cloudinary to get your env variables
---- Set .env variables 
---- CLOUDINARY_NAME=
     CLOUDINARY_API_KEY=
     CLOUDINARY_API_SECRET=
---- On the models.py of where you want to upload:
    import cloudinary 
    import cloudinary.uploader 
    import cloudinary.api 

    cloudinary.config(
        cloud_name=os.environ.get('CLOUDINARY_NAME'),
        api_key=os.environ.get('CLOUDINARY_API_KEY'),
        api_secret=os.environ.get('CLOUDINARY_API_SECRET')
    )