## cPanel Python App Guide | Step by Step

## Step 1 - Upload files
  -Upload your files to the system by using file manager as zip file
  
  -Extract files to the root dir

## Step 2 -DB Creation
  -Go to MySQL Databases from cPanel Tools
  
  -Create a DB
  
  -Create a User (and do NOT forgot Password)
  
  -Add user to the Database

## Step 3 -Python DB Settings
  -Go to your settings.py. Generally on "root"/core/settings.py
  
  -Change DATABASE settings (There is an example at the bottom of the page)

## Step 4 -Create Python App from cPanel
  -Select last version
  
  -Specify app root
  
  -Select url

## Step 5 -Terminal
  -Copy "source" code from cPnael python app page
  
  -Go to terminal and paste it
  
  -Install requirements
  
  Note: "pip install mysqlclient" can be problematic sometimes. In that case use "pip install mysql-connector-python"
  
  Example
```
pip install django
pip install Pillow
pip install django-colorfield
pip install django-heroku
pip install mysql-connector-python
```

## Step 6 -Edit passenger-wsgi.py
  -Delete all lines except imports and path.insert

  -Add "from core.wsgi import application"

## Step 7 -Terminal
```
python manage.py makemigrations
python manage.py migrate
```

-Restart Python Application

## Step 8 -Allowed Hosts
  -You may need to add you host to allowed hosts
  
  -Go to settings.py file
  
  -Add your host to ALLOWED_HOSTS line

  Example
  ```
  ALLOWED_HOSTS = ['https://www.example.com', 'www.example.com']
  ```
Restart Python Application Again

## settings.py, Database settings example

    DATABASES = {
        'default': {
            'NAME': 'DATEBASE_NAME',
            'ENGINE': 'mysql.connector.django',
            'USER': 'USERNAME',
            'PASSWORD': 'PASSWORD',
            'OPTIONS': {
              'autocommit': True,
            },
        }
    }

Admin panel superuser creation command

    python manage.py createsuperuser
