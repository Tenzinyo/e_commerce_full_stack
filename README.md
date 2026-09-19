--- All the command used for this project

-Backend and Frontend setup

- Step 1. Inside Backend folder:
    ---download dependencies
    - pip3 install  django djangorestframework psycopg2-binary python-dotenv
    --- create a backend folder inside the parent dir
    - django-admin startproject backend . 
    --- create a app folder and name it store since its e-commerce platform
    - python3 manage.py startapp store 

-  Step 2. Creating React in the parent dir
    - npm create vite@latest frontend
        -- not a command-- select REACT, Javascript and it will create the frontend process 
    -- not a command -- 
        - in the backend/settings.py -> go to installed_apps function and add all the - applications we downloaded - rest_framework, store (as the name of our app)

-  Step 3. Postgres sql
    - psql --version        
    - brew services start postgresql@16
    - brew update 
    - brew services list 
    - pg_isready
    -- create the postgres db
    - psql postgres
    --in the postgres console
    - CREATE ROLE (name of server) WITH LOGIN PASSWORD '(password)'
    -- then make superuser 
    - ALTER ROLE (name of server= postgres) SUPERUSER CREATEDB CREATEROLE;
    -- create database
    -- CREATE DATABASE (name_of_. db) OWNER postgres;
    - CREATE DATABASE ecommerce_db OWNER postgres;
    -- check db
    - \1

-  Step 4. Create .env file to store credentials for the postgresql
    -- in the env file have to fill 
    -  DB_NAME = ecommerce_db
    -  DB_USER = postgres
    -  DB_PASSWORD = postgres
    -  DB_HOST = localhost
    -   DB_PORT = 5432
    -- in the settings.py 
    --  code:
    -  import os
    -  from dotenv import load_dotenv
    -  load_dotenv()
        -- in databases under settings.py
        change .sqlite3 to postgresql and change the follwing code to
        DATABASES = 
            "default": 
                "ENGINE": "django.db.backends.postgresql",
                "NAME": os.getenv("DB_NAME"),
                "USER": os.getenv("DB_USER"),
                "PASSWORD": os.getenv("DB_PASSWORD"),
                "HOST": os.getenv("DB_HOST"),
                "PORT": os.getenv("DB_PORT"),
            
-  Step 5. Migrate the db in backend

    -  python3 manage.py migrate
    -- create superuser
    -  python3 manage.py createsuperuser
    -- now run application
    -  python3 manage.py runserver

