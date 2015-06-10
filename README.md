## Python Flask Skeleton for Google App Engine

## To Run Locally
1. If you dont already have  it, install [python 2.7](https://www.python.org/download/releases/2.7/)

2. You'll also want the package manager pip.  To get it, download [get-pip.py](https://bootstrap.pypa.io/get-pip.py) and then in the directory where it is run:
   ```
   python get-pip.py
   ```
3. Install the [App Engine Python SDK](https://developers.google.com/appengine/downloads).
See the README file for directions. 

4. Go to [appengine.google.com](https://console.developers.google.com/project) (sign up if need be) and create an new project. The id you give the project will be the your subdomain and application id. example:  your-app-id becomes your-app-id.appspot.com

4. Clone this repo with

   ```
   git clone https://github.com/GoogleCloudPlatform/appengine-python-flask-skeleton.git
   ```
5. Install dependencies in the project's lib directory. Only current lib we are including here is Flask (more below)
   Note: App Engine can only import libraries from inside your project directory.

   ```
   cd appengine-python-flask-skeleton
   pip install -r requirements.txt -t lib
   ```
6. Run this project locally from the command line:

   ```
   dev_appserver.py .
   ```

Visit the application [http://localhost:8080](http://localhost:8080)

See [the development server documentation](https://developers.google.com/appengine/docs/python/tools/devserver)
for options when running dev_appserver.

## Deploy
To deploy the application:

1. Edit the app.yaml file and set your-application-id-here to your app id

2. [Deploy the
   application](https://developers.google.com/appengine/docs/python/tools/uploadinganapp) with

   ```
   appcfg.py -A <your-project-id> --oauth2 update .
   ```
1. Congratulations!  Your application is now live at your-app-id.appspot.com

## Next Steps

### app.yaml

The [app.yaml](https://cloud.google.com/appengine/docs/python/config/appconfig) file is where you configure your application for appengine. For this app, we are setting the runtime to python27.

Also in the app.yaml file we set two handlers, /static  which will deliver any static files you put in those folders (like /static/js/react.js)

the second handler catches all other requests and sends them off to our python flask application in main.py, basically the place where out python code takes over.


### Flask
[Flask](http://flask.pocoo.org/) is a microframework for python. Read [the Quickstart guide](http://flask.pocoo.org/docs/0.10/quickstart/#quickstart) to find out more about it. You can kind of ignore everything up to the [routing section](http://flask.pocoo.org/docs/0.10/quickstart/#routing) since appengine handles running the app for you. Other than that, the docs are pretty good.

Long story short, you use a python attribute `@app.route('/hello')` to decorate functions and they become your web request handlers.

### Jinja
[Jinja](http://jinja.pocoo.org/) is a python template engine for generating html. You can use Flask's built in method [render_template](http://flask.pocoo.org/docs/0.10/api/#flask.render_template) to render files inside the /templates folder (it uses jinja by default).

To learn more read about the [template language](http://jinja.pocoo.org/docs/dev/templates/)

### AppEngine
Within the [Python Runtime](https://cloud.google.com/appengine/docs/python) there are a bunch of [services](https://cloud.google.com/appengine/docs/python/apis) you can take advantage of like identity, mail, memcache, search, sms, queues etc etc.

To then manage the prod version of this app, visit [appengine.google.com](https://appengine.google.com)


This skeleton includes `TODO` markers to help you find basic areas you will want
to customize.

### Relational Databases and Datastore
To add persistence to your models, use
[NDB](https://developers.google.com/appengine/docs/python/ndb/) for
scale.  Consider
[CloudSQL](https://developers.google.com/appengine/docs/python/cloud-sql)
if you need a relational database.

### Installing Libraries
See the [Third party
libraries](https://developers.google.com/appengine/docs/python/tools/libraries27)
page for libraries that are already included in the SDK.  To include SDK
libraries, add them in your app.yaml file. Other than libraries included in
the SDK, only pure python libraries may be added to an App Engine project.

### Feedback
Star this repo if you found it useful. Use the github issue tracker to give
feedback on this repo.

## Contributing changes
See [CONTRIB.md](CONTRIB.md)

## Licensing
See [LICENSE](LICENSE)

## Author
Logan Henriquez and Johan Euphrosine
