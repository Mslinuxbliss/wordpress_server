# wordpress_server
Code used in my Youtube video for setting up a wordpress web server

```
sudo apt update && sudo apt upgrade -y
sudo apt install apache2 php libapache2-mod-php mariadb-server mariadb-client php-mysql php-curl php-xml php-mbstring php-imagick php-zip php-gd

sudo mysql_secure_installation

sudo mysql
CREATE DATABASE wordpress_db;
GRANT ALL PRIVILEGES ON wordpress_db.* to wordpress_user@'localhost';
FLUSH PRIVILEGES;
exit

sudo cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/wordpress.conf
sudo nano /etc/apache2/sites-available/wordpress.conf

#change /var/www/html -> /var/www/wordpress

sudo a2ensite wordpress.conf
sudo a2dissite 000-default.conf
sudo systemctl restart apache2

cd /tmp
sudo wget  https://wordpress.org/latest.tar.gz
sudo tar -xzvf latest.tar.gz -C /var/www
sudo chown -R www-data.www-data /var/www/wordpress
```
