## Before run:

```
python3 -m venv venv
source venv/bin/activate
pip install --upgrade pip
pip install --upgrade setuptools
pip install -r requirements.txt
```


### Flask needs to be told how to import it, by setting the FLASK_APP environment variable:

```
export FLASK_APP=microblog.py
```
OR
write on .flaskenv:
FLASK_APP=microblog.py 


### How to run:

```
flask run --host=0.0.0.0 --port=2222
```


### The flask db sub-command is added by Flask-Migrate to manage everything related to database migrations:

```
flask db init
```
Remember that the flask command relies on the FLASK_APP environment variable to know where the Flask application lives. For this application, you want to set FLASK_APP to the value microblog.py

Since there is no previous database, the automatic migration will add the entire User model to the migration script.

```
flask db migrate -m "users table"
```

The `flask db migrate -m <name>` command does not make any changes to the database, it just generates the migration script. To apply the changes to the database, the `flask db upgrade` command must be used.