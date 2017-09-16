#### NOTE: While open-source, some features of this block explorer are not easily compatible with running your own version locally, and this is no longer recommended (except for expert users). ####

--


# Setup Instructions #

## Install ##


### Ubuntu ###

## Configure ##
- `$ cd` into your projects/workspaces directory and run `$ git clone https://github.com/blockcypher/explorer.git`. The result of `$ git remote -v` should look like this:
```
origin	git@github.com:blockcypher/explorer.git (fetch)
origin	git@github.com:blockcypher/explorer.git (push)
```
- `$ cd explorer/` to get to the project root direction, create a python3 virtual environment (`$ virtualenv -p python3 venv`) and then activate it (`$ source venv/bin/activate`)
- Install requirements: `$ pip3 install -r requirements.txt` (this will take a few mins)

## Run the Site Locally ##

Run the webserver locally:
```
$ ./manage.py makemigrations
$ ./manage.py migrate
$ ./manage.py runserver
```
You need to also run `ngrok` in the terminal (use the same `SITE_DOMAIN` from your `.env` file above):

download [ngrok](https://ngrok.com/download). unzip it and run
```
$ unzip /path/to/ngrok.zip
$ ./path/to/ngrok http 8000
```

Now visit http://pick_this_yourself.ngrok.io to confirm it's working (you could even do this on your phone)

## Check Out the Admin Section ##

- Create a superuser admin for yourself, by entering the following into `$ ./manage.py shell`:

```python
from users.models import AuthUser
AuthUser.objects.create_superuser(email='YOURCHOICE', password='PASSWORDGOESHERE')
```

Now visit http://pick_this_yourself.ngrok.io/admin