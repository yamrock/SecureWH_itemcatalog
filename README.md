# SecureWH_itemcatalog
Hardened Ubuntu server, apache webserver using wsgi mod to serve a flask app

###The IP address and SSH port :
52.24.66.8, SSH port : 2200

###The complete URL to your hosted web application:
http://52.24.66.8

###A summary of software installed and configuration changes made:
####Software installed:
* Apache web server
* PostgreSQL
* wsgi module for Apache
* SQLAlchemy
* Python PIP
* Git
* Dependencies for the application as described by this webapp's [readme] (https://github.com/yamrock/itemcatalog)
* fail2ban (SSH multiple failure logging/banning)
* monit (file and application server monitoring)

####Configuration changes
* Created a user called grader
* Updated sshd_config to listen on port 2200 instead of 22
* Configured UFW to restrict inbound access to 2200, 80 and NTP(123)
* Configured the local TZ to UTC
* Edited /etc/apache2/sites-enabled/000-default.conf to use /var/www/html/catalog.wsgi
* Created /var/www/html/catalog.wsgi to run the flask app
* Edited ~grader/itemcatalog/application.py, helper.py etc to remove relative links and replaced them with full paths
* Updated the app in developers.facebook.com to use the new url http://52.24.66.8
* Updated fail2ban's jail.conf in jail.local to enable monitoring for multiple unsuccessful SSH attempts on port 2200, and banning those IPs.
* Introduced a crontab to check for updates and upgrade the server weekly

###A list of any third-party resources 
http://flask.pocoo.org/docs/0.10/deploying/mod_wsgi/ : To integrate apache's wsgi module with flask app

http://stackoverflow.com : General troubleshooting

[Fail2ban tutorial](https://www.digitalocean.com/community/tutorials/how-to-protect-ssh-with-fail2ban-on-ubuntu-14-04)

[ubuntu cron](https://help.ubuntu.com/community/CronHowto)

[Monit configuration](https://mmonit.com/wiki/Monit/ConfigurationExamples)

