Building Continuous Integration/Delivery with Python
===

My current side project is to build and document a reusable foundation for continuous integration/delivery of a [twelve-factor](http://12factor.net/ "twelve-factor") web application written in Python.  I don't claim to be an authority.  I'm open to constructive criticism.

Much of this work will not strictly be programming.  There is a bit of work involved setting up the infrastructure to support good development processes.  However, having this in place will speed development and deployment later and encourage quality.  It pays off particularly well in a collaborative setting.

Some of the development infrastructure pieces:
* [Jenkins](https://jenkins-ci.org/ "Jenkins") as a test/build system
* [vSphere/ESXi](https://www.vmware.com/products/esxi-and-esx/overview "vSphere/ESXi") to host our servers
* [CentOS 7](https://www.centos.org/ "CentOS") base operating system
* [Docker](https://www.docker.com/ "Docker") for containers

Beyond the development infrastructure, non-programming tasks like building out the various components of the web application's technology stack and infrastructure will be performed.  We want to build an application which is prepared to scale well, so we'll attempt to make each component as stateless as possible to ease deployment of additional instances as necessary.  We'll work on the automation around these components (eg, monitoring of server resources, automatic deployment of new containers, automating cluster configuration changes).

Currently, the base components in mind to be configured for the backend for this project are:
 * [Django](https://www.djangoproject.com/ "Django") web framework for Python on [gunicorn](http://gunicorn.org/ "gunicorn") application server
 * [redis](http://redis.io/ "redis") for use with [django-channels](http://django-channels.readthedocs.org/en/latest/ "django-channels") for websockets
 * [PostgreSQL](http://www.postgresql.org/ "PostgreSQL") (or perhaps MariaDB/Galera) for the database
 * [NGINX](https://www.nginx.com/resources/wiki/ "NGINX") for static content and proxy to the application servers
 * [RabbitMQ](https://www.rabbitmq.com/ "RabbitMQ")/[Celery](http://www.celeryproject.org/ "Celery") for the task engine / background workers

Frontend components are still under consideration.  I have some experience with [AngularJS](https://angularjs.org/ "AngularJS") 1.x, but I want to look forward a bit so I may play some with [AngularJS 2 beta](https://angular.io/ "Angular 2 beta") or [React](https://facebook.github.io/react/ "React").  It seems like the future of javascript browser apps is pointing towards micro-libraries where you can swap out some core components more easily, so there might be a bit of mix and matching there, like using [redux](http://redux.js.org/ "redux") to manage state.  There will be some development tools in use on the frontend as well, such as [Gulp](http://gulpjs.com/ "Gulp") and [Bower](http://bower.io/ "Bower"), among others.