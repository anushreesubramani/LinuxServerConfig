# LinuxServerConfig
P5: Linux Server Configuration

The IP address is 52.37.208.198. The SSH port is 2200.
The application can be accessed from http://52.37.208.198/

I have updated all the packages, changed ssh port, setup firewall using ufw etc
I have installed the following software:  
Python  
Flask  
Postgresql  
Psycopg2  
SqlAlchemy  
Git  
Apache2  
Mod-wsgi  

List of commands executed to setup the server
# Create new user and give that user sudo access
adduser grader
su grader
visudo
# update all the existing packages
sudo apt-get update
sudo apt-get upgrade
#Change the timezone to UTC
sudo dpkg-reconfigure tzdata
#Make changes to ssh config to change ssh port to 2200 and allow 
# user grader ssh access and remove root login
sudo vim /etc/ssh/sshd_config
#restart the ssh server so that the changes reflect
sudo service ssh restart
# install ufw for setting up firewall
sudo apt-get install ufw
#check the current status of ufw
ufw status
#apply default setting to ufw
sudo ufw default deny incoming
sudo ufw default allow outgoing
# allow ssh via 2200, http in 80,ntp in 123 through the firewall
sudo ufw allow 2200
sudo ufw allow 80
sudo ufw allow 123
#check ufw status to see if the settings are OK
sudo ufw status
# Enable the firewall settings
sudo ufw enable
#check ufw status to see if the settings are OK
sudo ufw status
#install git
sudo apt-get install git
#install postgresql
sudo apt-get install postgresql postgresql-contrib
sudo -i -u postgres
#create user catalog in postgres 
createuser --interactive
sudo -i -u postgres
adduser catalog
sudo -i -u catalog
#install mod-wsgi package,python-dev,apache2
sudo apt-get install libapache2-mod-wsgi
sudo apt-get install python-dev
sudo apt-get install apache2
#enable mod-wsgi
sudo a2enmod wsgi
#restart apache
sudo service apache2 restart

After this, I cloned my project from github, created .wsgi file in my Catalog app,
made some configuration changes to apache2 and got my app up and running successfully.

References:
https://www.digitalocean.com/community/tutorials/how-to-deploy-a-flask-application-on-an-ubuntu-vps
Stackoverflow - lots of urls


