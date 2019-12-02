# LAMP setup

## Installation

Kernal
```
sudo apt-get update
sudo apt-get install apache2
sudo apt-get install mysql-server
sudo apt-get install php libapache2-mod-php php-mysql
sudo vim /etc/apache2/mods-enabled/dir.conf
```

dir.conf
```
<IfModule mod_dir.c>
	DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm
</IfModule>	
```
Change to:
```
<IfModule mod_dir.c>
	DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm
</IfModule>	
```

Kernal
```
sudo systemctl restart apache2
sudo apt install phpmyadmin
<Enter>
<PASSWORD>
<Enter>
sudo cp /etc/phpmyadmin/apache.conf /etc/apache2/conf-available/phpmyadmin.conf 
sudo a2enconf phpmyadmin
sudo systemctl restart apache2
```
## Troubleshoot

### Edit .htaccess

Kernel
```
sudo nano /var/www/html/.htaccess
```

.htaccess
```
# BEGIN WordPress
<IfModule mod_rewrite.c>
RewriteEngine On
RewriteBase /
RewriteRule ^index\.php$ - [L]
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /index.php [L]
</IfModule>
# END WordPress
```

Kernal
```
sudo service apache2 restart
```

### Edit apache.conf
Kernal
```
sudo nano /etc/apache2/apache.conf
```

apache.conf
```
<Directory /var/www/>
Options Indexes FollowSymLinks
AllowOverride None
Require all granted
</Directory>
```

CHANGE **None** TO **All** in apache.conf
```
<Directory /var/www/>
Options Indexes FollowSymLinks
AllowOverride All
Require all granted
</Directory>
```


### Rewrite a2enmod
Kernal
```
sudo a2enmod rewrite
```

Kernal
```
sudo service apache2 restart
```

