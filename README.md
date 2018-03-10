# Django app on Heroku
### Deploying steps

```heroku login```
* ##### It will ask you heroku account email and password

```cd project_root``` 
* ##### (project_root is file that has manage.py)

```heroku create```
* ##### It will create a new heroku app that has a random name(btw you can change it :)


* #### use pip install and following library name
```pip install```
    
* dj-database-url [docs](https://github.com/kennethreitz/dj-database-url)
* django-heroku [docs](https://github.com/heroku/django-heroku)
* gunicorn [docs](http://gunicorn.org)
* whitenoise [docs](http://whitenoise.evans.io/en/stable/)
* pipenv [docs](https://github.com/pypa/pipenv)


* #### run following command in project_root(project_root is file that has manage.py) after pipenv installed
```pipenv install```


* ##### Add following lines to settings.py(last line)

```
import django_heroku
django_heroku.settings(locals())
```
* ##### create Procfile(no- file extension. only Procfile). open and write following line
```
 web: gunicorn application_name.wsgi --log-file - 
```
* ##### (application_name is folder name which has wsgi file)

* ### if collectstatic error while pushing heroku, you can use following command
```
heroku config:set DISABLE_COLLECTSTATIC=1
python manage.py collectstatic
```
* #### Now it is time to push it
```
git push heroku master
```
* ##### if you are not working on master branch or if you get up-do-date warning you can use
```
git push heroku some-branch-name:master
```

* ##### after push and deploy is successful run following commands
* (if you did migrations before you pushed you repo)
```
heroku run python manage.py migrate
```
* (if you did not do migrations before you pushed you repo)
```
heroku run python manage.py makemigrations
heroku run python manage.py migrate
```

## Authors

* **Mevlana** - *Initial work* - [mevlanaayas](https://github.com/mevlanaayas)

## Acknowledgements

* I hope it works well for you. I ll be happy for any kinds of suggestions
