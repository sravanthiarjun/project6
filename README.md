# Linux-Server-Configuration

 In this project I deploy my build an item catalog project to an instance using a Linux server instance called Amazon Lightsail.
 
#### My server Details

   Server static IP Address 13.127.121.235
   
#### Grader Key

-----BEGIN RSA PRIVATE KEY-----

MIIEpQIBAAKCAQEA7EkNsz5WsXLu0Dg5E1A1+Py6Q0u61nTgCAJduqwc9JppB0oo
31fW6yR5WPebcr/auXZ18wgAeElAiBSauDDzGsjF5UC7OEnp//qIKrfbCEulx1x7
bt/iixiO4q9JEgsZaXmcnwa1ED//nFIqXbSNnfmNRZfDTfszZjyMvi73PqtxNPst
0N9UZ6NuKzdGpBQ6UWG0Zg5i3O61pjL7YBuMxBJTiCLRz0oFygzD5jZUPnLtuCsN
wy/eyk+xdXx9nC7FTKWB4EesyJ2QdOVJ6/vfC217s9N7QFxRkSt8Q5pCQ4mnqOlD
GFrMDAogX56UofpYdQ5jfQyJEJVetNYLnFP++QIDAQABAoIBAQChT8aApoB9KOAN
WzTsEIiocbGgG+V0X9pK3YKr3LDv9TLa/TAmOkvJwN7vdCu2DXD/yPYBc2cOt8PM
o3R1Z0Ww9XzVZHnsldmhHqMzts1cPnjxQBwst8BsAdoavFyAav9wWMwqbWPTsj2J
tTajPo6oWSSvbEqzxFl05MWZWWsGZqkoenas7x4iKjL6oIPyvWkHdD6OuoYVG2mQ
mVuXCiCyRXcxUILJ24HWWoRfwf7z/Sk+iteGL+AdlWPGYMptj78I0glYMPvKAM1U
yGkp73H83jykFRnoKPj++DTiC8lwFacvFyBcVDUhCskgrgtdR3RJM9wKm9e4qvtv
VjLYsa4BAoGBAP3aMCt7rnGQBmciEeMKL0MA+rjGunDhZ9rNQC+ky5UwMJRROuUf
pBlr/BfJOStPmQ0AeGCLkL3RJsoHgzymBJOk5r+l7f2Xd/orsYMkhwN+1IluvRhS
ZuqLoetXvmC+/3EtsLKSq9vzXu1opWIfsnCqYVet03d9BWuaOnLlDZoZAoGBAO5I
0U7NCepOs+tNvZghbA57Y0Zx8t3JfNxnWDqauSUQFmDNVLpJj1vTqrI2A3Me3ev0
6HupWXLDI20irET81ddi9tpt7H3dhtBaIOUruE4tAnIdEkdAkDmOsN/+YcWBS5CA
kDCPosbTCUYxU/dLEsPMah47Cw2LoMVUHOfgS+fhAoGBAJEhGMEDaOwMB10XIVrI
C9UmzjCtjRHUDGgPSE70zF9yuZNSDXXI7SyLjAidRk34p+vDBQ9NO2cKGD8QpHsb
/ynZ8QJIfxOocTNZn5b2XyokbKZV5U3ubmBRjDTcaT8ucyPll0vAhvis3uykE0lS
DdZT0msqOefqVhr6hcgCJBChAoGBALxu1SaNupOR3XHsrkvJ0lu5c45XugltttHM
39aoWFVY3Xl7ps8SMM4bGteHIz88X56is95m05ePfUpmqvh7QNftKO0fFG+MaXoG
bBEOe9dGfLKlDrlN8z+w+WqJDeRUFN+W62+bhsvYQ3NAuvfKZHJ2Ck0Rv/HcQy0J
ETrFAwHBAoGAOLXAwZFm12bnlH5kUN4cHVEx7D9aA7+25PwgE0eKwEZqV/JHBta6
C1NfqKOJSt3XKVfYSoUbe8oe8vWuk25ZqG5METmiRbICfl88oiz3I8Ky5A/3d5jv
YcLkoNg2oW0Bltbu6qKhxssFR5XBvOAGig74E3K9fZ5D+6Jb47glqK8=

-----END RSA PRIVATE KEY-----

#### Grader Password

unix

#### Step-1

1)Create an amazon account.

2)Create an instance in lightsail.aws.amazon.com

3)Download putty.exe,puttygen.exe in puti.org

--Open Putty. give staticIP of instance as hostname.

select file downloaded from shh-keys eg: LightsailDefaultPrivateKey-ap-south-1.pem click ok.then save private, yes, give some name.. save on desktop.then close it. now you will see a .ppk file on desktop.

From left tree, click on SSH. after, Auth. You will see browser button. click on browser, and select .ppk file and click on open. press No. username ubuntu

4)Create static ip in lightsail and download it.

5)Open putty enter your ip and add private key address.

6)Connect to grader by using the following command:

    ssh -i path/to/privatekey -p 2200 grader@ip address	
    
7)Creating grader User:

    sudo apt update 
    sudo apt upgrade
    sudo adduser grader
    
Follow the following steps:

    sudo nano /etc/sudoers		
    
Grant sudo permission to grader

    grader  ALL=(ALL:ALL) ALL	
    
8)We have to create a ssh key pair for grader

Open new terminal/command prompt and type

    ssh-keygen
    
This will generate public and private ssh keys which is saved to .ssh folder

9)Change ubuntu user to grader

    sudo su - grader
    
10)Create a new directory .ssh and new file authorized_keys in that directory

    mkdir .ssh
    sudo nano .ssh/authorized_keys
    
11)Permissions:

    chmod 700 .ssh	
    chmod 644 .ssh/authorized_keys
    
700 will give read write and execute permission to user.

644 prevent other user from writting in to file. Then restart ssh server

12)sudo service ssh restart

13)ssh -i .ssh/id_rsa grader@ipaddress

14)Now we have to change our port from 22 to 2200

    sudo nano /etc/ssh/sshd_config
    
Then change it.

15)Important thing is disabling ssh login as root

    sudo nano /etc/ssh/sshd_config
    
###### Make change PermitRootLogin no

16)Uncomplicated firewall(ufw) enbling:

    sudo ufw allow 2200/tcp
    sudo ufw allow 80/tcp
    sudo ufw allow 123/udp	
    sudo ufw enable
    
17)For viewing ports type:

    sudo ufw status	
    
18)Changing time Zone:

    sudo dpkg-reconfigure tzdata
    
#### Step-2

    Software Requirements:
    
AWS account with lightsail service activated.

1)Python Pip

2)Postgres

3)httplib2

4)SQLAlchemy

5)Apache2

6)Flask

7)Virtualenv

8)Requests

9)Oauth2client

##### Installation Process for softwares:

    sudo apt-get install apache2
    sudo apt-get install python-setuptools libapache2-mod-wsgi
    sudo a2enmod wsgi
    cd /var/www
    sudo mkdir FlaskApp
    sudo apt-get install git
    sudo apt-get install python-pip virtualenv
    sudo virtualenv venv
    sudo pip install Flask
    sudo pip install postgresql oauth2client httplib2 requests psycopg2
    cd /var/www/FlaskApp 
    sudo rm -r FlaskApp
    
Rename your repository to FlaskApp to init.py

    sudo mv project.py __init__.py
    
In that directory clone your github repository

    sudo git clone 'https://github.com/username/filename.git'
    
Check once your files added or not

Type ls

Changing database in both database_setup.py and init.py

    sudo nano database_setup.py

Copy the below code and paste it.

https://www.digitalocean.com/community/tutorials/how-to-deploy-a-flask-application-on-an-ubuntu-vps

Use this line to Replace database connection in init.py and database_setup.py

    engine = create_engine('postgresql://catalog:password@localhost/catalog')
    
Error : While accesssing the client_secrets.json file

PROJECT_ROOT = os.path.realpath(os.path.dirname(file))
json_url = os.path.join(PROJECT_ROOT, 'client_secrets.json')
CLIENT_ID = json.load(open(json_url))['web']['client_id']

Replace client_secrets.json with json_url in scriptfile

    sudo apt-get install postgresql
    sudo su - postgres
    psql
    
Now we have to create user

    CREATE USER catalog WITH PASSWORD 'password';
    ALTER USER catalog CREATEDB;
    CREATE DATABASE catalog WITH OWNER catalog;
    \c catalog  
    REVOKE ALL ON SCHEMA public FROM public;
    GRANT ALL ON SCHEMA public TO catalog;
    \q
    exit
    
#### Step-3

Configure and Enable a New Virtual Host, then type the following code in the shell.

    sudo nano /etc/apache2/sites-available/FlaskApp.conf

<VirtualHost *:80>
		ServerName mywebsite.com
		ServerAdmin admin@mywebsite.com
		WSGIScriptAlias / /var/www/FlaskApp/flaskapp.wsgi
		<Directory /var/www/FlaskApp/FlaskApp/>
			Order allow,deny
			Allow from all
		</Directory>
		Alias /static /var/www/FlaskApp/FlaskApp/static
		<Directory /var/www/FlaskApp/FlaskApp/static/>
			Order allow,deny
			Allow from all
		</Directory>
		ErrorLog ${APACHE_LOG_DIR}/error.log
		LogLevel warn
		CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

    sudo a2ensite FlaskApp
    sudo a2dissite 000-default.conf
    sudo nano flaskapp.wsgi
    
Then add the below code

#!/usr/bin/python
import sys
import logging
logging.basicConfig(stream=sys.stderr)
sys.path.insert(0,"/var/www/FlaskApp/")

from FlaskApp import app as application
application.secret_key = 'Add your secret key'

press ctrl+x and y

#### Step-4

Go to google console and change homeurl to

http://ipaddress.xip.io\callback

http://ipaddress.xip.io\gconnect

http://ipaddress.xip.io\login

#### FINAL STEP:

    sudo service apache2 restart
    
Then go to webbrowser and type your ipaddress finaly we get our project.

For error checking :

    sudo nano /var/log/apache2/error.log

#### OUTPUT:

CLICK HERE http://13.127.121.235.xip.io

#### Reference used:

https://www.digitalocean.com/community/tutorials/how-to-deploy-a-flask-application-on-an-ubuntu-vps
https://www.github.com




