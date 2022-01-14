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

