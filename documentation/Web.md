# Web

# Ajax, Web services, RESTful communication protocols

> These sit on top of HTTP, thus suffering from the same limitations as HTTP. Many of these protocols also require extensive processing and have a huge code size footprint. Many service providers promote the use of these protocols since their backend infrastructure is based on standard web servers that cannot handle any other type of protocol than HTTP.

# RESTful API (Representational State Transfer)

> In computing, representational state transfer (REST) is the software architectural style of the World Wide Web. REST's coordinated set of constraints, applied to the design of components in a distributed hypermedia system, can lead to a higher-performing and more maintainable software architecture. [Wikipedia](https://en.wikipedia.org/wiki/Representational_state_transfer)

> To the extent that systems conform to the constraints of REST they can be called RESTful. RESTful systems typically, but not always, communicate over Hypertext Transfer Protocol (HTTP) with the same HTTP verbs (GET, POST, PUT, DELETE, etc.) that web browsers use to retrieve web pages and to send data to remote servers.[4] REST systems interface with external systems as web resources identified by Uniform Resource Identifiers (URIs), for example /people/tom, which can be operated upon using standard verbs such as DELETE /people/tom. [Wikipedia](https://en.wikipedia.org/wiki/Representational_state_transfer) 

- [Learn REST: A Tutorial](http://rest.elkstein.org/)

## API Creation

> Creating and exposing APIs allows your web application to interact with other applications through machine-to-machine communication. API creation frameworks... [FullStackPython](http://www.fullstackpython.com/api-creation.html)

## Flask

> Flask is a microframework for Python based on Werkzeug, Jinja 2 and good intentions. [Flask Homepage](http://flask.pocoo.org/)

> It’s time to write your first REST API. This guide assumes you have a working understanding of Flask, and that you have already installed both Flask and Flask-RESTful. [Here]([http://flask-restful-cn.readthedocs.org/en/0.3.4/quickstart.html)

[Browsable Web APIs for Flask](http://www.flaskapi.org/)

```sh
    root@board:~# pip install Flask
    Downloading/unpacking Flask
      Downloading Flask-0.10.1.tar.gz (544kB): 544kB downloaded
    Installing collected packages: Flask
    Successfully installed Flask
    Cleaning up...
    root@board:~# 
```

## Flask-RESTful

> Flask-RESTful is an extension for Flask that adds support for quickly building REST APIs. It is a lightweight abstraction that works with your existing ORM/libraries. Flask-RESTful encourages best practices with minimal setup. If you are familiar with Flask, Flask-RESTful should be easy to pick up. [Flask-RESTful Documentation](http://flask-restful.readthedocs.org/en/latest/index.html)

```sh
    root@board:~# pip install flask-restful
    Downloading/unpacking flask-restful
      Downloading Flask-RESTful-0.3.5.tar.gz (102kB): 102kB downloaded
    Downloading/unpacking aniso8601>=0.82 (from flask-restful)
      Downloading aniso8601-1.1.0.tar.gz (49kB): 49kB downloaded
    Downloading/unpacking python-dateutil (from aniso8601>=0.82->flask-restful)
      Downloading python-dateutil-2.5.1.tar.gz (235kB): 235kB downloaded
    Installing collected packages: flask-restful, aniso8601, python-dateutil
    Successfully installed flask-restful aniso8601 python-dateutil
    Cleaning up...
    root@board:~# 
```

## Project

```sh
    root@board:~# vi mainflask.py
```

```python
#!/usr/bin/python
from flask import Flask
from flask_restful import Api, Resource

app = Flask(__name__)
api = Api(app)

class Network(Resource):
    def get(self):
        data = 'Network Data'
        return data

api.add_resource(Network, '/network')

if __name__ == '__main__':
    app.run(debug=True)
```

```sh
    root@board:~# python mainflask.py
     * Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)
     * Restarting with stat
     * Debugger is active!
     * Debugger pin code: 331-202-890
```

Connect to your boardipaddress:5000 in a web browser

```sh
    127.0.0.1 - - [28/Dec/2015 15:07:38] "GET /network HTTP/1.1" 200 -
    127.0.0.1 - - [28/Dec/2015 15:07:40] "GET /network HTTP/1.1" 200 -
```