# SecureWH_itemcatalog
Hardened Ubuntu server, apache webserver using wsgi mod to serve a flask app

###The IP address and SSH port :
52.24.66.8, SSH port : 2200

###The complete URL to your hosted web application:
http://52.24.66.8

###A summary of software you installed and configuration changes made:
####Software installed:
* Apache web server
* PostgreSQL
* wsgi module for Apache
* SQLAlchemy
* Python PIP
* Git
* Dependencies for the application as described by this webapp [readme] (https://github.com/yamrock/itemcatalog)

####Configuration changes
* Created a user called grader
* Updated sshd_config to listen on port 2200 instead of 22
* Configured UFW to restrict inbound access to 2200, 80 and NTP(123)
* Configured the local TZ to UTC
* Edited /etc/apache2/sites-enabled/000-default.conf to use /var/www/html/catalog.wsgi
* Created /var/www/html/catalog.wsgi to run the flask app
* Edited ~grader/itemcatalog/application.py, helper.py etc to remove relative links and replaced them with full paths
* Updated the app in developers.facebook.com to use the new url http://52.24.66.8

###A list of any third-party resources 
http://flask.pocoo.org/docs/0.10/deploying/mod_wsgi/ : To integrate apache's wsgi module with flask app
http://stackoverflow.com : General troubleshooting

