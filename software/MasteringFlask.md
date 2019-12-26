![cover](https://img9.doubanio.com/view/subject/l/public/s28356714.jpg)

    作者: Jack Stouffer
    出版社: Packt Publishing
    副标题: Gain expertise in Flask to create dynamic and powerful web applications
    出版年: 2015-9-30
    页数: 282
    定价: USD 49.99
    装帧: Paperback
    ISBN: 9781784393656

[豆瓣链接](https://book.douban.com/subject/26680328/)

- [The beginning of our project](#the-beginning-of-our-project)
  - [Using Flask Script](#using-flask-script)
- [Creating Models with SQLAlchemy](#creating-models-with-sqlalchemy)
  - [Setting up SQLAlchemy](#setting-up-sqlalchemy)
    - [Python packages](#python-packages)
    - [Flask SQLAlchemy](#flask-sqlalchemy)
    - [Our first model](#our-first-model)
    - [Creating the user table](#creating-the-user-table)
  - [CRUD](#crud)
    - [Creating models](#creating-models)
    - [Reading models](#reading-models)
      - [FILTERING QUERIES](#filtering-queries)
    - [Updating models](#updating-models)
    - [Deleting models](#deleting-models)
  - [Relationships between models](#relationships-between-models)
  - [The convenience of SQLAlchemy sessions](#the-convenience-of-sqlalchemy-sessions)
  - [Database migrations with Alembic](#database-migrations-with-alembic)
- [Creating Controllers with Blueprints](#creating-controllers-with-blueprints)
  - [Request setup, teardown, and application globals](#request-setup-teardown-and-application-globals)
  - [Error pages](#error-pages)
  - [Class-based views](#class-based-views)
    - [Method class views](#method-class-views)
  - [Blueprints](#blueprints)
- [Advanced Application Structure](#advanced-application-structure)
  - [The project as a module](#the-project-as-a-module)
    - [Refactoring the code](#refactoring-the-code)
  - [Application factories](#application-factories)
- [Securing Your App](#securing-your-app)
  - [Setting up](#setting-up)
    - [Updating the models](#updating-the-models)
    - [reCAPTCHA](#recaptcha)
    - [Creating views](#creating-views)
    - [Social logins](#social-logins)
      - [OPENID](#openid)
      - [FACEBOOK](#facebook)
  - [Using the session](#using-the-session)
  - [Flask Login](#flask-login)
    - [User roles](#user-roles)
- [Building RESTful APIs](#building-restful-apis)
  - [Setting up a RESTful Flask API](#setting-up-a-restful-flask-api)
- [Creating Asynchronous Tasks with Celery](#creating-asynchronous-tasks-with-celery)
  - [What is Celery?](#what-is-celery)
  - [Setting up Celery and RabbitMQ](#setting-up-celery-and-rabbitmq)
  - [Creating tasks in Celery](#creating-tasks-in-celery)
  - [Running Celery tasks](#running-celery-tasks)
    - [Celery workflows](#celery-workflows)
      - [PARTIALS](#partials)
      - [CALLBACKS](#callbacks)
      - [GROUP](#group)
      - [CHAIN](#chain)
      - [CHORD](#chord)
      - [RUNNING TASKS PERIODICALLY](#running-tasks-periodically)
- [Useful Flask Extensions](#useful-flask-extensions)
  - [Flask Script](#flask-script)
  - [Flask Debug Toolbar](#flask-debug-toolbar)
  - [Flask Cache](#flask-cache)
  - [Flask Assets](#flask-assets)
  - [Flask Admin](#flask-admin)
  - [Flask Mail](#flask-mail)
- [Testing Flask Apps](#testing-flask-apps)
  - [Unit testing the application](#unit-testing-the-application)
    - [Testing the route functions](#testing-the-route-functions)
  - [User interface testing](#user-interface-testing)
  - [Test coverage](#test-coverage)

# The beginning of our project
config.py

```py
class Config(object):
    pass

class ProdConfig(Config):
    pass

class DevConfig(Config):
    DEBUG = True
```

main.py

```py
from flask import Flask
from config import DevConfig

app = Flask(__name__)
app.config.from_object(DevConfig)

@app.route('/')
def home():
    return '<h1>Hello World!</h1>'

if __name__ == '__main__':
    app.run()
```

We use `from_object` because in future, multiple configurations will be used, and manually changing every variable when we need to switch between configurations is tedious.

## Using Flask Script
```
$ pip install flask-script
```

manage.py

```py
from flask.ext.script import Manager, Server
from main import app

manager = Manager(app)
manager.add_command("server", Server())

@manager.shell
def make_shell_context():
    return dict(app=app)

if __name__ == "__main__":
    manager.run()
```

Use the shell with:

```sh
$ python manage.py shell
# Lets check if our app imported correctly
>>> app
<Flask 'main'>
```

# Creating Models with SQLAlchemy
## Setting up SQLAlchemy
### Python packages
```
$ pip install flask-sqlalchemy
```

We will also need to install specific packages for the database you chose to use that will act as the connector for SQLAlchemy.

```
# MySQL
$ pip install PyMySQL
# Postgres
$ pip install psycopg2
# MSSQL
$ pip install pyodbc
# Oracle
$ pip install cx_Oracle
```

### Flask SQLAlchemy
It takes the general form of the following:

```
databasetype+driver://user:password@ip:port/db_name
```

For each driver you installed previously, the URI would be:

```
# SQLite
sqlite:///database.db
# MySQL
mysql+pymysql://user:password@ip:port/db_name
# Postgres
postgresql+psycopg2://user:password@ip:port/db_name
# MSSQL
mssql+pyodbc://user:password@dsn_name
# Oracle
oracle+cx_oracle://user:password@ip:port/db_name
```

config.py:

```py
class DevConfig(Config):
    debug = True
    SQLALCHEMY_DATABASE_URI = "YOUR URI"
```

### Our first model
In our `main.py` file, SQLAlchemy must first be initialized with our app as follows:

```py
from flask.ext.sqlalchemy import SQLAlchemy

app = Flask(__name__)
app.config.from_object(DevConfig)
db = SQLAlchemy(app)
```

Let's create a `User` model to interact with a user table in the `main.py` file:

```py
class User(db.Model):
    id = db.Column(db.Integer(), primary_key=True)
    username = db.Column(db.String(255))
    password = db.Column(db.String(255))

    def __init__(self, username):
        self.username = username

    def __repr__(self):
        return "<User '{}'>".format(self.username)
```

To tell SQLAlchemy what name to use, add the `__tablename__` class variable.

```py
class User(db.Model):
    __tablename__ = 'user_table_name'

    id = db.Column(db.Integer(), primary_key=True)
    username = db.Column(db.String(255))
    password = db.Column(db.String(255))
```

### Creating the user table
Update `manage.py` to:

```py
from main import app, db, User
...
@manager.shell
def make_shell_context():
    return dict(app=app, db=db, User=User)

Style - "db","User" in first line as Code Highlight
```

This will allow us to work with our models in the shell. Run the shell now and use `db.create_all()` to create all of the tables:

```py
$ python manage.py shell
>>> db.create_all()
```

## CRUD
### Creating models
To create a new row in your database using our models, add the model to the `session` and `commit` objects.

```py
>>> user = User(username='fake_name')
>>> db.session.add(user)
>>> db.session.commit()
```

### Reading models
After we have added data to our database, data can be queried using `Model.query`.

For our first example, use `all()` to get all rows in the database as a list.

```py
>>> users = User.query.all()
>>> users
[<User 'fake_name'>]

>>> users = User.query.limit(10).all()

# asending
>>> users = User.query.order_by(User.username).all()
# desending
>>> users = User.query.order_by(User.username.desc()).all()

>>> user = User.query.first()
>>> user.username
fake_name

>>> user = User.query.get(1)
>>> user.username
fake_name

>>> users = User.query.order_by(
        User.username.desc()
    ).limit(10).first()

>>> Post.query.paginate(1, 10)
<flask_sqlalchemy.Pagination at 0x105118f50>
```

#### FILTERING QUERIES
```py
>>> users = User.query.filter_by(username='fake_name').all()

>>> users = User.query.order_by(User.username.desc())
        .filter_by(username='fake_name')
        .limit(2)
        .all()

>>> user = User.query.filter(
        User.id > 1
    ).all()

>>> from sqlalchemy.sql.expression import not_, or_
>>> user = User.query.filter(
           User.username.in_(['fake_name']),
           User.password == None
       ).first()
# find all of the users with a password
>>> user = User.query.filter(
           not_(User.password == None)
       ).first()
# all of these methods are able to be combined
>>> user = User.query.filter(
           or_(not_(User.password == None), User.id >= 1)
       ).first()
```

### Updating models
```py
>>> User.query.filter_by(username='fake_name').update({
            'password': 'test'
        })
# The updated models have already been added to the session
>>> db.session.commit()
```

### Deleting models
```py
>>> user = User.query.filter_by(username='fake_name').first()
>>> db.session.delete(user)
>>> db.session.commit()
```

## Relationships between models
- One-to-many
- Many-to-many

## The convenience of SQLAlchemy sessions
First, the session is the handler for `transactions`.

Second, the session makes it impossible for there to be two different references to the same row in the database.

## Database migrations with Alembic
`Alembic`, which automatically creates and tracks database migrations from the changes in our SQLAlchemy models. Database migrations are records of all the changes of our schema. Alembic allows us to upgrade or downgrade our database to a specific saved version.

We won't work directly with Alembic; instead, we will use `Flask-Migrate`.

```
$ pip install Flask-Migrate
```

manage.py:

```py
from flask.ext.script import Manager, Server
from flask.ext.migrate import Migrate, MigrateCommand

from main import app, db, User, Post, Tag

migrate = Migrate(app, db)

manager = Manager(app)
manager.add_command("server", Server())
manager.add_command('db', MigrateCommand)


@manager.shell
def make_shell_context():
    return dict(app=app, db=db, User=User, Post=Post, Tag=Tag)

if __name__ == "__main__":
    manager.run()
```

# Creating Controllers with Blueprints
## Request setup, teardown, and application globals
In some cases, a request-specific variable is needed across all view functions and needs to be accessed from the template as well. To achieve this, we can use Flask's decorator function `@app.before_request` and the object `g`. The function `@app.before_request` is executed every time before a new request is made. The Flask object `g` is a thread-safe store of any data that needs to be kept for each specific request. At the end of the request, the object is destroyed, and a new object is spawned at the start of a new request.

For example, the following code checks whether the Flask `session` variable contains an entry for a logged in user; if it exists, it adds the `User` object to `g`:

```py
from flask import g, session, abort, render_template

@app.before_request
def before_request():
    if ‘user_id’ in session:
        g.user = User.query.get(session[‘user_id’])

@app.route(‘/restricted’)
def admin():
    if g.user is None:
        abort(403)
    return render_template(‘admin.html’)
```

## Error pages
Displaying a browser's default error pages to the end user is jarring as the user loses all context of your app, and they must hit the back button to return to your site. To display your own templates when an error is returned with the Flask `abort()` function, use the `errorhandler` decorator function:

```py
@app.errorhandler(404)
def page_not_found(error):
    return render_template('page_not_found.html'), 404
```

## Class-based views
```py
from flask.views import View

class GenericView(View):
    def __init__(self, template):
        self.template = template
        super(GenericView, self).__init__()

    def dispatch_request(self):
        return render_template(self.template)

app.add_url_rule(
    '/', view_func=GenericView.as_view(
        'home', template='home.html'
    )
)
```

- `dispatch_request()` This is the function in our view that acts as the normal view function and returns an HTML string.
- The `app.add_url_rule()` function mimics the `app.route()` function as it ties a route to a function call.
  - The first argument defines the route of the function, and the view_func parameter defines the function that handles the route.
  - The View.as_view() method is passed to the view_func parameter because it transforms the View class into a view function.
    - The first argument defines the name of the view function, so functions such as url_for() can route to it.
    - The remaining parameters are passed to the `__init__` function of the View class.

Like the normal view functions, HTTP methods other than GET must be explicitly allowed for the View class. To allow other methods, a class variable containing the list of named methods must be added:

```py
class GenericView(View):
    methods = ['GET', 'POST']
    …
    def dispatch_request(self):
        if request.method == ‘GET’:
            return render_template(self.template)
        elif request.method == ‘POST’:
            …
```

### Method class views
```py
@app.route('/user', methods=['GET', 'POST', 'PUT', 'DELETE'])
def users():
    if request.method == 'GET':
        …
    elif request.method == 'POST':
        …
    elif request.method == 'PUT':
        …
    elif request.method == 'DELETE':
        …
```

This can be solved with the MethodView class. MethodView allows each method to be handled by a different class method to separate concerns:

```py
from flask.views import MethodView

class UserView(MethodView):
    def get(self):
        …
    def post(self):
        …
    def put(self):
        …
    def delete(self):
        …

app.add_url_rule(
    '/user',
    view_func=UserView.as_view('user')
)
```

## Blueprints
`Blueprints` provide a way of combining groups of views with common functionality and allow developers to break their app down into different components. In our architecture, blueprints will act as our `controllers`.

A blueprint acts much like a Flask app object, but is not actually a self-contained app.

```py
from flask import Blueprint
example = Blueprint(
    'example',
    __name__,
    template_folder='templates/example',
    static_folder='static/example',
    url_prefix="/example"
)

@example.route('/')
def home():
    return render_template('home.html')
```

- The blueprint takes two required parameters—the name of the blueprint and the name of the package—that are used internally in Flask; passing `__name__` to it will suffice.
- The other parameters are optional and define where the blueprint will look for files. Because `templates_folder` was specified, the blueprint will not look in the default template folder, and the route will render `templates/example/home.html` and not `templates/home.html`. The `url_prefix` option automatically adds the provided URI to the start of every route in the blueprint. So, the URL for the home view is actually `/example/`.

The `url_for()` function will now have to be told which blueprint the requested route is in:

```
{{ url_for('example.home') }}
```

Also, the `url_for()` function will now have to be told whether the view is being rendered from within the same blueprint:

```
{{ url_for('.home') }}
```

The `url_for()` function will also look for static files in the specified static folder.

To add the blueprint to our app:

```py
app.register_blueprint(example)
```

Let's transform our current app to one that uses blueprints. We will first need to define our blueprint before all of our routes:

```py
blog_blueprint = Blueprint(
    'blog',
    __name__,
    template_folder='templates/blog',
    url_prefix="/blog"
)
```

Now, because the templates folder was defined, we need to move all of our templates into a subfolder of the templates folder named blog. Next, all of our routes need to have the `@app.route` changed to `@blog_blueprint.route`, and any class view assignments now need to be registered to blog_blueprint. Remember that `url_for()` function calls in the templates will also have to be changed to have a period prepended to then to indicate that the route is in the same blueprint.

At the end of the file, right before the `if __name__ == '__main__':` statement, add the following:

```py
app.register_blueprint(blog_blueprint)
```

Now all of our content is back on the app, which is registered under the blueprint. Because our base app no longer has any views, let's add a redirect on the base URL:

```py
@app.route('/')
def index():
    return redirect(url_for('blog.home'))
```

Why blog and not `blog_blueprint`? Because blog is the name of the blueprint and the name is what Flask uses internally for routing. `blog_blueprint` is the name of the variable in the Python file.

# Advanced Application Structure
## The project as a module
```
webapp/
  config.py
  database.db
  main.py
  manage.py
  env/
  migrations/
    versions/
  static/
    css/
    js/
  templates/
    blog/
```

To convert our code to a module, our files will be converted to this folder structure:

```
webapp/
  manage.py
  database.db
  webapp/
    __init__.py
    config.py
    forms.py
    models.py
    controllers/
      __init__.py
      blog.py
    static/
      css/
      js/
    templates/
      blog/
  migrations/
    versions/
```

### Refactoring the code
Your `models.py` file should now look like this:

```py
from flask.ext.sqlalchemy import SQLAlchemy

db = SQLAlchemy()

tags = db.Table(
    'post_tags',
    db.Column('post_id', db.Integer, db.ForeignKey('post.id')),
    db.Column('tag_id', db.Integer, db.ForeignKey('tag.id'))
)

class User(db.Model):
    …

class Post(db.Model):
    …

class Comment(db.Model):
    …

class Tag(db.Model):
    …
```

The forms.py file should look like this:

```py
from flask_wtf import Form
from wtforms import StringField, TextAreaField
from wtforms.validators import DataRequired, Length


class CommentForm(Form):
    …
```

The blog.py file should now look like this:

```py
import datetime
from os import path
from sqlalchemy import func
from flask import render_template, Blueprint

from webapp.models import db, Post, Tag, Comment, User, tags
from webapp.forms import CommentForm

blog_blueprint = Blueprint(
    'blog',
    __name__,
    template_folder=path.join(path.pardir, 'templates', 'blog')
    url_prefix="/blog"
)

def sidebar_data():
    …
```

With the db.init_app() function, we will add the app object to the db object after it's imported:

```py
from flask import Flask, redirect, url_for
from config import DevConfig

from models import db
from controllers.blog import blog_blueprint

app = Flask(__name__)
app.config.from_object(DevConfig)

db.init_app(app)

@app.route('/')
def index():
    return redirect(url_for('blog.home'))

app.register_blueprint(blog_blueprint)

if __name__ == '__main__':
    app.run()
```

Because the SQLAlchemy URL for a SQLite database is a relative file path, it has to be changed to:

```py
from os import path

class DevConfig(object):
    SQLALCHEMY_DATABASE_URI = 'sqlite://' + path.join(
        path.pardir,
        'database.db'
    )
```

To fix the manage.py imports, replace the imports from main.py with:

```py
from webapp import app
from webapp.models import db, User, Post, Tag, Comment
```

## Application factories
Creating a factory function for our application object has several benefits. First, it allows the context of the environment to change the configuration of the application. When your server creates the application object to serve, it can take into account any changes in the server necessary and change the configuration object given to the app accordingly. Second, it makes testing much easier because it allows differently configured applications to be tested quickly. Third, multiple instances of the same application using the same configuration can be created very easily.

Now that the benefits of application factories are clear, let's modify our `__init__.py` file to implement it:

```py
from flask import Flask, redirect, url_for
from models import db
from controllers.blog import blog_blueprint

def create_app(object_name):
    app = Flask(__name__)
    app.config.from_object(object_name)

    db.init_app(app)

    @app.route('/')
    def index():
        return redirect(url_for('blog.home'))

    app.register_blueprint(blog_blueprint)

    return app
```

We will need to modify our manage.py file in order to work with the create_app function as follows:

```py
import os
from flask.ext.script import Manager, Server
from flask.ext.migrate import Migrate, MigrateCommand
from webapp import create_app
from webapp.models import db, User, Post, Tag, Comment

# default to dev config
env = os.environ.get('WEBAPP_ENV', 'dev')
app = create_app('webapp.config.%sConfig' % env.capitalize())
…
manager = Manager(app)
manager.add_command("server", Server())
```

# Securing Your App
## Setting up
### Updating the models
To protect our user passwords, they will be encrypted with a one-way encryption method named a `hashing algorithm`.

`Bcrypt` is purposely designed to be inefficient and slow (milliseconds vs. microseconds) for the computer to process, thereby making it harder to brute force.

```
$ pip install Flask-Bcrypt
```

To hold all future extensions, add the file named extensions.py in the same directory as the `__init__.py` file. Inside, Flask Bcrypt will have to be initialized:

```py
from flask.ext.bcrypt import Bcrypt
bcrypt = Bcrypt()
```

It is then added to the app object:

```py
from webapp.extensions import bcrypt

def create_app(object_name):
    app = Flask(__name__)
    app.config.from_object(object_name)

    db.init_app(app)
    bcrypt.init_app(app)
```

To have our User object use bcrypt, we will add two methods that set the password and check if a string matches the stored hash:

```py
from webapp.extensions import bcrypt

class User(db.Model):
    id = db.Column(db.Integer(), primary_key=True)
    username = db.Column(db.String(255))
    password = db.Column(db.String(255))
    posts = db.relationship(
        'Post',
        backref='user',
        lazy='dynamic'
    )

    def __init__(self, username):
        self.username = username

    def __repr__(self):
        return '<User {}>'.format(self.username)

    def set_password(self, password):
        self.password = bcrypt.generate_password_hash(password)

    def check_password(self, password):
        return bcrypt.check_password_hash(self.password, password)
```

### reCAPTCHA
The registration form will have a username field, a password field with a confirmation field, and a special field named a `reCAPTCHA` field. A `CAPTCHA` is a special field on a web form that checks whether whoever is entering data into the form is actually a person, or an automated program that is spamming your site. reCAPTCHA is simply one implementation of a CAPTCHA.

To use reCAPTCHA, you will need a reCAPTCHA login from https://www.google.com/recaptcha/intro/index.html. As reCAPTCHA is a Google product, you can log in with your Google account.

![1](https://www.safaribooksonline.com/library/view/mastering-flask/9781784393656/graphics/B03929_06_01.jpg)

Add these keys to the config object in the config.py file so that WTForms can access them as follows:

### Creating views
That was alright for one view. Now, this section is going to add many views on the base URL of the site. As such, we need a new controller in controllers/main.py:

```py
main_blueprint = Blueprint(
    'main',
    __name__,
    template_folder='../templates/main'
)

@main_blueprint.route('/')
def index():
    return redirect(url_for('blog.home'))
```

In the main.py controller, add the following:

```py
from webapp.forms import LoginForm, RegisterForm

@main_blueprint.route('/login', methods=['GET', 'POST'])
def login():
    form = LoginForm()

    if form.validate_on_submit():
        flash("You have been logged in.", category="success")
        return redirect(url_for('blog.home'))

    return render_template('login.html', form=form)

@main_blueprint.route('/logout', methods=['GET', 'POST'])
def logout():
    flash("You have been logged out.", category="success")
    return redirect(url_for('.home'))

@main_blueprint.route('/register', methods=['GET', 'POST'])
def register():
    form = RegisterForm()

    if form.validate_on_submit():
        new_user = User()
        new_user.username = form.username.data
        new_user.set_password(form.username.data)

        db.session.add(new_user)
        db.session.commit()

        flash(
            "Your user has been created, please login.",
            category="success"
        )

           return redirect(url_for('.login'))

    return render_template('register.html', form=form)
```

### Social logins
#### OPENID
`OpenID` is an open protocol that allows users on one site to be authenticated by any third-party site that implements the protocol, which are called `Relaying Parties (RPs)`.

```
$ pip install Flask-OpenID
```

In the extensions.py file, the OpenID object can be initialized as follows:

```py
from flask.ext.bcrypt import Bcrypt
from flask.ext.openid import OpenID
bcrypt = Bcrypt()
oid = OpenID()
```

In the `__init__.py` file, the oid object is registered to the app object:

```py
from .models import db

def create_app(object_name):
    app = Flask(__name__)
    app.config.from_object(object_name)

    db.init_app(app)
    bcrypt.init_app(app)
    oid.init_app(app)
```

The new form object will only need the URL of the RP:

```py
from wtforms.validators import DataRequired, Length, EqualTo, URL

class OpenIDForm(Form):
    openid = StringField('OpenID URL', [DataRequired(), URL()])
```

On the login and registration views, OpenIDForm() will be initialized, and if the data is valid, a login request will be sent:

```py
from webapp.extensions import oid
…

@main_blueprint.route('/login', methods=['GET', 'POST'])
@oid.loginhandler
def login():
    form = LoginForm()
    openid_form = OpenIDForm()

    if openid_form.validate_on_submit():
        return oid.try_login(
            openid_form.openid.data,
            ask_for=['nickname', 'email'],
            ask_for_optional=['fullname']
        )

    if form.validate_on_submit():
        flash("You have been logged in.", category="success")
        return redirect(url_for('blog.home'))

    openid_errors = oid.fetch_error()
    if openid_errors:
        flash(openid_errors, category="danger")

    return render_template(
       'login.html',
       form=form,
       openid_form=openid_form
    )

@main_blueprint.route('/register', methods=['GET', 'POST'])
@oid.loginhandler
def register():
    form = RegisterForm()
    openid_form = OpenIDForm()

    if openid_form.validate_on_submit():
        return oid.try_login(
            openid_form.openid.data,
            ask_for=['nickname', 'email'],
            ask_for_optional=['fullname']
        )

    if form.validate_on_submit():
        new_user = User(form.username.data)
        new_user.set_password(form.password.data)

        db.session.add(new_user)
        db.session.commit()

        flash(
            "Your user has been created, please login.",
            category="success"
        )

        return redirect(url_for('.login'))

    openid_errors = oid.fetch_error()
    if openid_errors:
        flash(openid_errors, category="danger")

    return render_template(
        'register.html',
        form=form,
        openid_form=openid_form
    )
```

To handle the user creation and login, a new function in the extensions.py file is needed:

```py
@oid.after_login
def create_or_login(resp):
    from models import db, User
    username = resp.fullname or resp.nickname or resp.email
    if not username:
        flash('Invalid login. Please try again.', 'danger')
        return redirect(url_for('main.login'))

    user = User.query.filter_by(username=username).first()
    if user is None:
        user = User(username)
        db.session.add(user)
        db.session.commit()

    # Log the user in here
    return redirect(url_for('blog.home'))
```

#### FACEBOOK
```
$ pip install Flask-OAuth
```

![fcebook](https://www.safaribooksonline.com/library/view/mastering-flask/9781784393656/graphics/B03929_06_04.jpg)

Use these values while adding the following code to extensions.py:

```py
from flask_oauth import OAuth

bcrypt = Bcrypt()
oid = OpenID()
oauth = OAuth()

…

facebook = oauth.remote_app(
    'facebook',
    base_url='https://graph.facebook.com/',
    request_token_url=None,
    access_token_url='/oauth/access_token',
    authorize_url='https://www.facebook.com/dialog/oauth',
    consumer_key=' FACEBOOK_APP_ID',
    consumer_secret=' FACEBOOK_APP_SECRET',
    request_token_params={'scope': 'email'}
)
@facebook.tokengetter
def get_facebook_oauth_token():
    return session.get('facebook_oauth_token')
```

In the main.py controller, add the following code:

```py
from webapp.extensions import oid, facebook
…

@main_blueprint.route('/facebook')
def facebook_login():
    return facebook.authorize(
        callback=url_for(
            '.facebook_authorized',
            next=request.referrer or None,
            _external=True
        )
    )


@main_blueprint.route('/facebook/authorized')
@facebook.authorized_handler
def facebook_authorized(resp):
    if resp is None:
        return 'Access denied: reason=%s error=%s' % (
            request.args['error_reason'],
            request.args['error_description']
        )

    session['facebook_oauth_token'] = (resp['access_token'], '')

    me = facebook.get('/me')
    user = User.query.filter_by(
        username=me.data['first_name'] + " " + me.data['last_name']
    ).first()

    if not user:
        user = User(me.data['first_name'] + " " + me.data['last_name'])
        db.session.add(user)
        db.session.commit()

    # Login User here
    flash("You have been logged in.", category="success")

    return redirect(
        request.args.get('next') or url_for('blog.home')
    )
```

## Using the session
One way to create authentication in Flask is to use the `session` object. The session object is an object in Flask that creates an easy way for the server to store information in the user's browser with cookies.

To log a user in, a username key will be added to the session and set to the username of the current user.

```py
@main_blueprint.route('/login', methods=['GET', 'POST'])
def login():
    form = LoginForm()

    if form.validate_on_submit():
        # Add the user's name to the cookie
        session['username'] = form.username.data

    return render_template('login.html', form=form)
```

To log the user out, the key can be popped from the session:

```py
@main_blueprint.route('/logout', methods=['GET', 'POST'])
def logout():
    # Remove the username from the cookie
    session.pop('username', None)
    return redirect(url_for('.login'))
```

To check whether a user is currently logged in, the view can test if the username key exists in the session. Consider the following new post view:

```py
@blog_blueprint.route('/new', methods=['GET', 'POST'])
def new_post ():
    if 'username' not in session:
        return redirect(url_for('main.login'))
    …
```

Some of our templates will need access to the current user object.

```py
@blog_blueprint.before_request
def check_user():
    if 'username' in session:
        g.current_user = User.query.filter_by(
            username=session['username']
        ).one()
    else:
        g.current_user = None
```

Our login check can be changed to:

```py
@blog_blueprint.route('/new', methods=['GET', 'POST'])
def new_post():
    if not g.current_user:
        return redirect(url_for('main.login'))
    …
```

Also, the edit button on the post page should only appear when the current user is the author:

```py
{% if g.current_user == post.user %}
<div class="row">
  <div class="col-lg-2">
    <a href="{{ url_for('.edit_post', id=post.id) }}" class="btn btn-
      primary">Edit</a>
  </div>
</div>
{% endif %}
```

The edit page itself should also perform the following check:

```py
@blog_blueprint.route('/edit/<int:id>', methods=['GET', 'POST'])
def edit_post(id):
    if not g.current_user:
        return redirect(url_for('main.login'))

    post = Post.query.get_or_404(id)

    if g.current_user != post.user:
        abort(403)
    …
```

## Flask Login
```
$ pip install flask-login
```

Initialize the LoginManager object in extensions.py:

```py
from flask.ext.login import LoginManager
…
login_manager = LoginManager()
```

There are some configuration options that need to be changed on the object:

```py
login_manager.login_view = "main.login"
login_manager.session_protection = "strong"
login_manager.login_message = "Please login to access this page"
login_manager.login_message_category = "info"

@login_manager.user_loader
def load_user(userid):
    from models import User
    return User.query.get(userid)
```

This app will use a simple implementation for this functionality:

```py
from flask.ext.login import AnonymousUserMixin
…

class User(db.Model):
    id = db.Column(db.Integer(), primary_key=True)
    username = db.Column(db.String(255))
    password = db.Column(db.String(255))
    posts = db.relationship(
        'Post',
        backref='user',
        lazy='dynamic'
    )

    def __init__(self, username):
        self.username = username

    def __repr__(self):
        return '<User {}>'.format(self.username)

    def set_password(self, password):
        self.password = bcrypt.generate_password_hash(password)

    def check_password(self, password):
        return bcrypt.check_password_hash(self.password, password)

    def is_authenticated(self):
        if isinstance(self, AnonymousUserMixin):
            return False
        else:
            return True

    def is_active(self):
        return True

    def is_anonymous(self):
        if isinstance(self, AnonymousUserMixin):
            return True
        else:
            return False

    def get_id(self):
        return unicode(self.id)
```

### User roles
To add user permissions to our application, our User model will need a many-to-many relationship to a Role object, and it will need another Flask extension named `Flask Principal`.

```py
roles = db.Table(
    'role_users',
    db.Column('user_id', db.Integer, db.ForeignKey('user.id')),
    db.Column('role_id', db.Integer, db.ForeignKey('role.id'))
)

class User(db.Model):
    id = db.Column(db.Integer(), primary_key=True)
    username = db.Column(db.String(255), unique=True)
    password = db.Column(db.String(255))
    posts = db.relationship(
        'Post',
        backref='user',
        lazy='dynamic'
    )
    roles = db.relationship(
        'Role',
        secondary=roles,
        backref=db.backref('users', lazy='dynamic')
    )

    def __init__(self, username):
        self.username = username

        default = Role.query.filter_by(name="default").one()
        self.roles.append(default)
    …

class Role(db.Model):
    id = db.Column(db.Integer(), primary_key=True)
    name = db.Column(db.String(80), unique=True)
    description = db.Column(db.String(255))

    def __init__(self, name):
        self.name = name

    def __repr__(self):
        return '<Role {}>'.format(self.name)
```

In extensions.py, Flask Principal will be initialized and our RoleNeed objects will be created:

```py
from flask.ext.principal import Principal, Permission, RoleNeed
principals = Principal()
admin_permission = Permission(RoleNeed('admin'))
poster_permission = Permission(RoleNeed('poster'))
default_permission = Permission(RoleNeed('default'))
```

Flask Principal requires a function that adds Need objects to it after the identity has changed. Because this function requires access to the app object, this function will reside in the `__init__.py` file:

```py
from flask.ext.principal import identity_loaded, UserNeed, RoleNeed
from extensions import bcrypt, oid, login_manager, principals
def create_app(object_name):
    app = Flask(__name__)
    app.config.from_object(object_name)

    db.init_app(app)
    bcrypt.init_app(app)
    oid.init_app(app)
    login_manager.init_app(app)
    principals.init_app(app)

    @identity_loaded.connect_via(app)
    def on_identity_loaded(sender, identity):
        # Set the identity user object
        identity.user = current_user

        # Add the UserNeed to the identity
        if hasattr(current_user, 'id'):
            identity.provides.add(UserNeed(current_user.id))

        # Add each role to the identity
        if hasattr(current_user, 'roles'):
            for role in current_user.roles:
                identity.provides.add(RoleNeed(role.name))
     …
```

Now when the identity is changed, it will add a UserNeed and all of the RoleNeed objects as well. The identity changes when the user logs in or logs out:

```py
from flask.ext.principal import (
    Identity,
    AnonymousIdentity,
    identity_changed
)

@main_blueprint.route('/login', methods=['GET', 'POST'])
@oid.loginhandler
def login():
    …

    if form.validate_on_submit():
        user = User.query.filter_by(
            username=form.username.data
        ).one()
        login_user(user, remember=form.remember.data)

        identity_changed.send(
            current_app._get_current_object(),
            identity=Identity(user.id)
        )

        flash("You have been logged in.", category="success")
        return redirect(url_for('blog.home'))

@main_blueprint.route('/logout', methods=['GET', 'POST'])
def logout():
    logout_user()

    identity_changed.send(
        current_app._get_current_object(),
        identity=AnonymousIdentity()
    )

    flash("You have been logged out.", category="success")
    return redirect(url_for('.login'))
```

When the user logs in, their identity will trigger the on_identity_loaded method, and set their Need objects up. Now if we had a page that we wanted only posters to have access to:

```py
from webapp.extensions import poster_permission
@blog_blueprint.route('/edit/<int:id>', methods=['GET', 'POST'])
@login_required
@poster_permission.require(http_exception=403)
def edit_post(id):
    …
```

We could also replace our user check in the same view with a UserNeed check as follows:

```py
from webapp.extensions import poster_permission, admin_permission

@blog_blueprint.route('/edit/<int:id>', methods=['GET', 'POST'])
@login_required
@poster_permission.require(http_exception=403)
def edit_post(id):
    post = Post.query.get_or_404(id)
    permission = Permission(UserNeed(post.user.id))

    # We want admins to be able to edit any post
    if permission.can() or admin_permission.can():
        form = PostForm()

        if form.validate_on_submit():
            post.title = form.title.data
            post.text = form.text.data
            post.publish_date = datetime.datetime.now()

            db.session.add(post)
            db.session.commit()

            return redirect(url_for('.post', post_id=post.id))

        form.text.data = post.text
        return render_template('edit.html', form=form, post=post)

    abort(403)
```

# Building RESTful APIs
## Setting up a RESTful Flask API
```
$ pip install Flask-Restful
```

In the extensions.py file, initialize the Api object that will handle all the routes:

```py
from flask.ext.restful import Api
…
rest_api = Api()
```

The control logic and views for our Post API should be stored in a new folder named rest in the controllers folder. In this folder, we will need an empty `__init__.py` and a file named post.py. Inside post.py, let's create a simpleHello World example:

```py
from flask.ext.restful import Resource

class PostApi(Resource):
    def get(self):
        return {'hello': 'world'}
```

Just like the other Flask extensions we used, the Api object will need to be initialized on the app object in the `__init__.py` file, which holds the create_app function. The PostApi class will also have its route defined with the add_resource() method of the Api object:

```py
from .extensions import (
    bcrypt,
    oid,
    login_manager,
    principals,
    rest_api
)
from .controllers.rest.post import PostApi

def create_app(object_name):
    …
    rest_api.add_resource(PostApi, '/api/post')
    rest_api.init_app(app)
```

# Creating Asynchronous Tasks with Celery
## What is Celery?
Celery is an asynchronous task queue written in Python.Celery runs tasks, which are user-defined functions, concurrently—multiple tasks at once—through the Python multiprocessing library. Celery receives messages that tell it to start a task from a broker, which is usually called a message queue as shown in the following diagram:

![1](https://www.safaribooksonline.com/library/view/mastering-flask/9781784393656/graphics/B03929_09_01.jpg)

## Setting up Celery and RabbitMQ

```
$ pip install Celery
$ pip install Flask-Celery-Helper
```

## Creating tasks in Celery
```py
class DevConfig(Config):
    DEBUG = True
    SQLALCHEMY_DATABASE_URI = 'sqlite:///../database.db'
    CELERY_BROKER_URL = "amqp://guest:guest@localhost:5672//"
    CELERY_BACKEND = "amqp://guest:guest@localhost:5672//"
```

In the extensions.py file, the Celery class from Flask-Celery-Helper will be initialized:

```py
from flask.ext.celery import Celery
celery = Celery()
```

In a new file in the top-level directory, the same location where manage.py resides, named celery_runner.py, add the following:

```py
import os
from webapp import create_app
from celery import Celery
from webapp.tasks import log

def make_celery(app):
    celery = Celery(
        app.import_name,
        broker=app.config['CELERY_BROKER_URL'],
        backend=app.config['CELERY_BACKEND_URL']
    )
    celery.conf.update(app.config)
    TaskBase = celery.Task

    class ContextTask(TaskBase):
        abstract = True

        def __call__(self, *args, **kwargs):
            with app.app_context():
                return TaskBase.__call__(self, *args, **kwargs)

    celery.Task = ContextTask

    return celery

env = os.environ.get('WEBAPP_ENV', 'dev')
flask_app = create_app(
    'webapp.config.%sConfig' % env.capitalize()
)
celery = make_celery(flask_app)
```

Now, we can write our first task. It will be a simple task to start with, one that just returns any string passed to it. In a new file in the application directory named `tasks.py`, add the following:

```py
from webapp.extensions import celeryfrom webapp.extensions import celery
@celery.task()
def log(msg):
    return msg
```

Now, the final piece of the puzzle is to run the Celery process, which is called a `worker`, in a new terminal window.

```py
$ celery worker -A celery_runner --loglevel=info
```

Now, we can send commands to our Celery worker. Open the manage.py shell and import the log task:

```py
>>> from webapp.tasks import log
>>> log("Message")
Message
>>> result = log.delay("Message")
```

However, calling the delay method on the task will send a message to the worker process to execute the function with the given arguments.

With any asynchronous task, the `ready` method can be used to tell if the task has successfully completed. If true, the `get` method can be used to retrieve the result of the tasks.

```py
>>> result.ready()
True
>>> result.get()
"Message"
```

When a task is run on the Celery worker, the `state` of the task can be accessed via the state attribute.The available states are as follows:

- FAILURE: The task failed and all of the retries failed as well
- PENDING: The task has not yet been received by the worker
- RECEIVED: The task has been received by the worker and is not yet processing
- RETRY: The task failed and is waiting to be retried
- REVOKED: The task was stopped
- STARTED: The worker has started processing the task
- SUCCESS: The task completed successfully

In Celery, if a task fails, then the task can recall itself with the retry method as follows:

```py
@celery.task(bind=True)
def task(self, param):
    try:
        some_code
    except Exception, e:
        self.retry(exc=e)
```

The `bind` parameter in the decorator function tells Celery to pass a reference to the task object as the first parameter in the function. Using the `self` parameter, the `retry` method can be called, which will rerun the task with the same parameters. There are several other parameters that can be passed to the function decorator to change the behavior of the task:

- max_retries: This is the maximum number of times the task can be retried before it is declared as failed.
- default_retry_delay: This is the time in seconds to wait before running the task again. It's a good idea to keep this at somewhere around a minute or so if you expect that the conditions that led to the task failing are transitory—for example, network errors.
- rate_limit: This specifies the total number of unique calls to this task that are allowed to run in a given interval. If the value is an integer, it is the total number of this task that is allowed to run per second. The value can also be a string in the form of x/m for x number of tasks per minute or x/h for x number of tasks per hour. For example, passing in 5/m will only allow this task to be called five times a minute.
- time_limit: If specified, the task will be killed if it runs longer than this number of seconds.
- ignore_result: If the task's return value isn't used, then don't send it back.

## Running Celery tasks
### Celery workflows
Consider the following task:

```py
@celery.task()
def multiply(x, y):
    return x * y
```

Let's see a `signature` in action to understand it. Open up the `manage.py` shell:

```py
>>> from celery import signature
>>> from webapp.tasks import multiply
# Takes the same keyword args as apply_async
>>> signature('webapp.tasks.multiply', args=(4, 4) , countdown=10)
webapp.tasks.multiply(4, 4)
# same as above
>>> from webapp.tasks import multiply
>>> multiply.subtask((4, 4), countdown=10)
webapp.tasks.multiply(4, 4)
# shorthand for above, like delay in that it doesn't take
# apply_async's keyword args
>>> multiply.s(4, 4)
webapp.tasks.multiply(4, 4)
>>> multiply.s(4, 4)()
16
>>> multiply.s(4, 4).delay()
```

#### PARTIALS
```py
>>> new_multiply = multiply(2)
>>> new_multiply(5)
10
# The first function is unaffected
>>> multiply(2, 2)
4
```

#### CALLBACKS
```py
>>> multiply.apply_async((4, 4), link=log.s())
```

#### GROUP
The group function takes a list of signatures and creates a callable function to execute all of the signatures in parallel and then return a list of all of the results:

```py
>>> from celery import group
>>> sig = group(multiply.s(i, i+5) for i in range(10))
>>> result = sig.delay()
>>> result.get()
[0, 6, 14, 24, 36, 50, 66, 84, 104, 126]
```

#### CHAIN
The chain function takes task signatures and passes the value of each result to the next value in the chain, returning one result as follows:

```py
>>> from celery import chain
>>> sig = chain(multiply.s(10, 10), multiply.s(4), multiply.s(20))
# same as above
>>> sig = (multiply.s(10, 10) | multiply.s(4) | multiply.s(20))
>>> result = sig.delay()
>>> result.get()
8000
```

#### CHORD
The chord function creates a signature that will execute a group of signatures and pass the final result to a callback:

```py
>>> from celery import chord
>>> sig = chord(
    group(multiply.s(i, i+5) for i in range(10)),
    log.s()
)
>>> result = sig.delay()
>>> result.get()
[0, 6, 14, 24, 36, 50, 66, 84, 104, 126]
```

#### RUNNING TASKS PERIODICALLY
To add periodic tasks, add the following to the DevConfig configuration object:

```py
import datetime
…

CELERYBEAT_SCHEDULE = {
    'log-every-30-seconds': {
        'task': 'webapp.tasks.log',
        'schedule': datetime.timedelta(seconds=30),
        'args': ("Message",)
    },
}
```

For very specific intervals, there is the Celery `crontab` object.To illustrate how the crontab object represents intervals, here are some examples:

```py
>>> from celery.schedules import crontab
# Every midnight
>>> crontab(minute=0, hour=0)
# Once a 5AM, then 10AM, then 3PM, then 8PM
>>> crontab(minute=0, hour=[5, 10, 15, 20])
# Every half hour
>>> crontab(minute='*/30')
# Every Monday at even numbered hours and 1AM
>>> crontab(day_of_week=1, hour ='*/2, 1')
```

- Monitoring Celery
- Creating a reminder app
- Creating a weekly digest

# Useful Flask Extensions
## Flask Script

In Flask Script, you can create custom commands to be run within the application context. All that is needed is to create a command to decorate a normal Python function with a decorator function provided by Flask Script. For example, if we wanted a task that would return the string "Hello, World!" we would add the following to manage.py:

```py
@manager.command
def test():
    print "Hello, World!"
```

From the command line, the test command can now be run using the following:

```py
$ python manage.py test
Hello, World!
```

Flask Script also provides two utility functions that can be easily added to our project.

```py
from flask.ext.script.commands import ShowUrls, Clean
…
manager = Manager(app)
manager.add_command("server", Server())
manager.add_command("show-urls", ShowUrls())
manager.add_command("clean", Clean())
```

## Flask Debug Toolbar
```
$ pip install flask-debugtoolbar
```

## Flask Cache
Flask Cache solves this problem by allowing us to store the results of our view functions and return the stored results rather than render the template again.

```
$ pip install Flask-Cache
```

## Flask Assets
The main technique that developers use is to concatenate all of the JavaScript libraries into one file and all of the CSS libraries into another while removing all of the whitespace and carriage returns from the resulting files.

```
$ pip install Flask-Assets cssmin jsmin
```

## Flask Admin
This is such a common requirement for apps that a Flask extension name Flask Admin was created to easily create administrator interfaces.

```
$ pip install Flask-Admin
```

## Flask Mail
The final Flask extension that this chapter will cover is Flask Mail, which allows you to connect and configure your SMTP client from Flask's configuration.

```
$ pip install Flask-Mail
```

# Testing Flask Apps
## Unit testing the application

In this configuration, we will use the Python `tempfile` module in the standard library in order to create a test SQLite database in a file that will automatically delete itself when the tests are over.

```py
import tempfile

class TestConfig(Config):
    db_file = tempfile.NamedTemporaryFile()

    DEBUG = True
    DEBUG_TB_ENABLED = False

    SQLALCHEMY_DATABASE_URI = 'sqlite:///' + db_file.name

    CACHE_TYPE = 'null'
    WTF_CSRF_ENABLED = False

    CELERY_BROKER_URL = "amqp://guest:guest@localhost:5672//"
    CELERY_BACKEND_URL = "amqp://guest:guest@localhost:5672//"

    MAIL_SERVER = 'localhost'
    MAIL_PORT = 25
    MAIL_USERNAME = 'username'
    MAIL_PASSWORD = 'password'
```

### Testing the route functions
```py
class TestURLs(unittest.TestCase):
    def setUp(self):
        # Bug workarounds
        admin._views = []
        rest_api.resources = []

        app = create_app('webapp.config.TestConfig')
        self.client = app.test_client()

        # Bug workaround
        db.app = app

        db.create_all()
```

## User interface testing
```
$ pip install selenium
```

```py
import unittest
from selenium import webdriver
class TestURLs(unittest.TestCase):
    def setUp(self):
        self.driver = webdriver.Firefox()
    def tearDown(self):
        self.driver.close()
```

## Test coverage
```
$ pip install coverage
```