# Project 1

**Installing Apache and Updating the Firewall** 
___

updating a list of packages in package manager

`$ sudo apt update`

![](images/sudoaptupdate1.png)

running apache2 package installation

`$ sudo apt install apache2`

![](images/sudoaptinstallapache2.png)

![](images/sudoaptinstallapache22.png)

verifing that apache2 is running as a service in my OS

`$ sudo systemctl status apache2`

![](images/sudosystemctlstatusapache23.png)

opening TCP port 80 in the EC2 instance

![](images/TCPport804.png)

accessing apache2 locally

`$ curl http://localhost:80`

![](images/localhost5.png)

retrieving public IP address locally

`$ curl -s http://169.254.169.254/latest/meta-data/public-ipv4`

![](images/curlipv6.png)

test that apache server is up and running using http://3.86.200.246

![](images/ubuntufirstpage7.png)

**Installing MySQL**

installing mysql in the server

`$ sudo apt install mysql-server`

![](images/installmysqlserver8.png)

securing sql installation

` $ sudo mysql_secure_installation`

![](images/mysqlsecureinstallation9.png)

logging into mysql server

` $ sudo mysql`

![](images/sudomysql10.png)

**Installing PHP**

installing 3 PHP packages - *PHP, Libapache2-mod-php & Php-mysql*

` $ sudo apt install php libapache2-mod-php php-mysql`

![](images/installingphp11.png)

confirming php version

` $ php -v`

![](images/php-v12.png)

**LAMP Stack is installed and operational**

### Creating a virtual host for my website using Apache2

creating a directory for projectlamp

` $ sudo mkdir /var/www/projectlamp`

assigning ownership of the directory with my current system user

` $  sudo chown -R $USER:$USER /var/www/projectlamp`

Creating and opening a new configuration file in Apache’s sites-available directory using "vi" command-line editor

` $ sudo vi /etc/apache2/sites-available/projectlamp.conf`

entering bare-bones configuration by hitting on i on the keyboard to get into the insert mode, and pasted the texts:

![](images/virtualhost8013.png)

showing the new file in the sites-available directory

`$ sudo ls /etc/apache2/sites-available`

![](images/mkdirprojectlamp14.png)

enabling the new virtual host

`$ sudo a2ensite projectlamp`

disabling the default website that comes installed with Apache

` $ sudo a2dissite 000-default`

![](images/z2ensite+dissite15.png)

testing to make sure configuration file does not contain syntax error

`$ sudo apache2ctl configtest`

reloading Apache so changes made can take effect

`$ sudo systemctl reload apache2`

Creating an index.html file in the /var/www/projectlamp location to test if the virtual host works

`sudo echo 'Hello LAMP from hostname' $(curl -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' $(curl -s http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectlamp/index.html`

proof that it's working

![](images/hellolamp16.png)

**Enabling PHP on the Website**

editing the /etc/apache2/mods-enabled/dir.conf file and changing the order in which the index.php file is listed within the DirectoryIndex directive to make the php page the landing page

`$ sudo vim /etc/apache2/mods-enabled/dir.conf`

![](images/ifmodule17.png)

Creating a new file named index.php inside the custom web root folder

`$ vim /var/www/projectlamp/index.php`

![](images/phpinfo18.png)

reloading Apache to effect change

`$ sudo systemctl reload apache2`

![](images/apache2modsenabled19.png)

output to show that PHP installation is working

![](images/final20.png)