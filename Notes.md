# Django for Beginners ch4

## Creating database models

Django turns models into a database table for us. And this is done using the models module that's imported into `models.py`. `TextField` is used to specify what kind of content the model will hold. Several model fields are supported in django.

## Activating models

After models have been created, django needs to be updated in two ways:

1. Create a migration file with the `makemigrations` command which generates SQL commands for preinstalledapps in the INSTALLED-APP settings in `settings.py`
   > Note: Migration files do no execute those commands on our database file, rahter are a arefernce of all new changes ot our models. This helps to maintain a record of changes made to the models over time.
2. Build the actual database with the `migrate` command which executes the instructions in our migrations file.

> Note: The commands `migarte` and `makemigrations` would apply to all available changes

## Django Admin

Django provides with a robust admin interface for interacting with the database.

To use the admin we first need to create a superuser who can login. This is done using the `createsuperuser` command and responding to the prompts appropriately.

Adding str() methods to all of your model is a best practice to improve readabilty

## View/Templates/URLs

In listing the content of the database we use the generic class-based `ListView` which returns an ogject called `object_list`

## Tests

Since the homepage works with a database we use `TestCase` which will let us create a 'test' database that can be checked against. This means that tests do not need to be run on the actual databse but instead can make a separate test database, fill it with sample data and then test against it.

> Note: It is important that all test methods start with `test_` so as to let django know to test them.

The first test was on the model, but the second test is on the only page: the homepage. Specifically, the test is to show that it exists, uses the `home` view and uses the `home.html` template i.e status code response = 200.

> **Note:** A new import of `reverse` was added at the top

> **Also Note:** That the response says 4 tests, this is becuase 'setUp' isn't an actual test but merely lets us run subsequent tests. The 4 actual tests are test_text_content, test_view_url_exists_at_proper_location,test_view_url_by_name, and test_view_uses_correct_template
> Any function that uses the word 'test' at the beginning and exists in a tests.py file will be run at the command `python manage.py test`

## Heroku deployment

1. Update Pipfile.lock with the command `pipenv lock`
2. Make new Procfile with `touch Procfile` in bash shell and write `web: gunicorn {projectname}.esgi --log-file -` in it.
3. Install gunicorn with `pipenv install gunicorn`
4. Update settings.py such that `ALLOWED_HOSTS = ['*]`
5. Push to git repo i.e Add, Commit, Push trio
6. Log in to Heroku with `heroku login`
7. Create the app with `heroku create`
8. Set git to use the app name when code is pushed to Heroku with `heroku git:remote -a {app name}`
9. Ignore static files with `heroku config:set DISABLE_COLLECTSTATIC=1`
10. Push code to Heroku with `git push heroku master`
11. Add free scaling so it's actually running online with `heroku ps:scale web=1`
