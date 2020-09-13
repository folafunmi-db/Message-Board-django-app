# Django for Beginners ch4

## Creating database models
Django turns models into a database table for us. And this is done using the models module that's imported into `models.py`. `TextField` is used to specify what kind of content the model will hold. Several model fields are supported in django.

## Activating models
After models have been created, django needs to be updated in two ways:
1. Create a migration file with the `makemigrations` command which generates SQL commands for preinstalledapps in the INSTALLED-APP settings in `settings.py`
   >Note: Migration files do no execute those commands on our database file, rahter are a arefernce of all new changes ot our models. This helps to maintain a record of changes made to the models over time.
2. Build the actual database with the `migrate` command which executes the instructions in our migrations file.
