# Project: Linux Server Configuration (Full Stack Web Developer Nanodegree)

<a href="https://www.udacity.com/">
  <img src="https://s3-us-west-1.amazonaws.com/udacity-content/rebrand/svg/logo.min.svg" width="300" alt="Udacity logo">
</a>


My last project for courses [Full Stack Web Developer Nanodegree program](https://www.udacity.com/course/full-stack-web-developer-nanodegree--nd004)

### Server Info
IP: 3.95.21.170     
Port SSH: 2200     
WebApp: [http://3.95.21.170.xip.io/](http://3.95.21.170.xip.io/)     

### List of software installed
 - PostgreSQL     
 - htop     
 - Apache     
 - Python
 - Python pip
 - Python pip libs
 - git
 
### List of commands executed in server
 
 Update all currently installed packages.      
 ```
 sudo apt-get update
 sudo apt-get upgrade
 ```   
 
 Install finger     
 ```sudo apt-get install finger```   
 
 Install python and dependences   
 ```
 sudo apt-get install build-essential checkinstall
 sudo apt-get install libreadline-gplv2-dev libncursesw5-dev libssl-dev libsqlite3-dev tk-dev libgdbm-dev libc6-dev libbz2-dev
 cd /usr/src
 sudo wget https://www.python.org/ftp/python/2.7.16/Python-2.7.16.tgz
 sudo tar xzf Python-2.7.16.tgz
 cd Python-2.7.16
 sudo ./configure --enable-optimizations
 sudo make altinstall
 ```
 
 Create user and add secury for server   
 ```
 sudo adduser grader
 sudo nano /etc/sudoers.d/grader
 cd /home/grader/
 mkdir .ssh
 sudo touch .ssh/authorized_keys
 sudo nano .ssh/authorized_keys
 sudo chmod 700 .ssh
 sudo chmod 644 .ssh/authorized_keys
 sudo nano /etc/ssh/sshd_config
 sudo service ssh restart
 sudo ufw default deny incoming
 sudo ufw default allow outgoing
 sudo ufw allow ssh
 sudo ufw allow 2200/tcp
 sudo ufw allow www
 sudo ufw allow 123/tcp
 ```
 
 Install apache and configure for python web app
 ```
sudo apt-get install apache2
sudo apt-get install libapache2-mod-wsgi
sudo nano /etc/apache2/sites-enabled/000-default.conf
```

Install postgresql, create user and database for project
```
sudo apt-get install postgresql
sudo -u postgres -i
psql
postgres=# create database mydb;
postgres=# create user catalog with encrypted password 'catalog';
postgres=# grant all privileges on database mydb to catalog;
```

Get and configure web app
```
git clone https://github.com/ruiblaese/udacity-fsnd-project-item-catalog
cd udacity-fsnd-project-item-catalog/vagrant/
sudo cp -r catalog/ /var/www/html/
cd /var/www/html/catalog/
sudo apt install python-pip
sudo pip2 install --upgrade pip
sudo pip2 install flask packaging oauth2client redis passlib flask-httpauth
sudo pip2 install sqlalchemy flask-sqlalchemy psycopg2-binary bleach requests
sudo pip install Flask-SeaSurf==0.2.2
```

### Resources used
 - [Udacity Nanodegree Program Full Stack Web Developer ](https://www.udacity.com/course/full-stack-web-developer-nanodegree--nd004)
 - [Udacity Course Linux Command Line Basics](https://www.udacity.com/course/linux-command-line-basics--ud595)
 - [Udacity Course Configuring Linux Web Servers](https://www.udacity.com/course/configuring-linux-web-servers--ud299)
 - [How to Install Python 2.7.16 on Ubuntu & LinuxMint](https://tecadmin.net/install-python-2-7-on-ubuntu-and-linuxmint/)
 - [Instalando e configurando o Apache no Linux / Install and configure Apache in Linux](http://www.devfuria.com.br/linux/instalando-apache-via-yum-apt-get/)
 - [Instalando o módulo WSGI / Install module WSGI](http://www.devfuria.com.br/linux/instalando-apache-wsgi/)
 - [Python Flask Fazendo deploy com Apache / Deploy Python Flash with Apache](http://www.devfuria.com.br/python/flask-apache/)
 - [How to Install Pip on Ubuntu 18.04](https://linuxize.com/post/how-to-install-pip-on-ubuntu-18.04/)
 - [How to Kill a Process from the Command Line](https://www.linux.com/learn/intro-to-linux/2017/5/how-kill-process-command-line)
 - [What is the difference between apt-get update and upgrade?*](https://askubuntu.com/questions/94102/what-is-the-difference-between-apt-get-update-and-upgrade)
  - [Ubuntu Server message says packages can be updated, but apt-get does not update any*](https://serverfault.com/questions/265410/ubuntu-server-message-says-packages-can-be-updated-but-apt-get-does-not-update)

These were the links I remembered, if I remember other links I will add later    
*Udacity, thanks for the tip   


### Others
Maybe I have forgotten some commands, I had several small problems in the middle of the setup that made me go to the internet several times.


## Author & Supporting 
ruiblaese@gmail.com
