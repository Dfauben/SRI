# Tema 1 - Servidores Web

## Actividad #1

### La arquitectura Web es un modelo compuesto de tres capas, ¿cuáles son y cuál es  la función de cada una de ellas?

### Una plataforma web es el entorno de desarrollo de software empleado para  diseñar y ejecutar un sitio web; destacan dos plataformas web, LAMP y WISA. Explica en qué consiste cada una de ellas.

### Instalación de Apache en Ubuntu

1.

````
sudo -i
````
`````
apt update
`````

`````
apt install apache2
`````

`````
ufw app list
`````

`````
ufw allow "Apache"
`````

``
https://localhost
``

### Instalación de MySQL

`````
apt install mysql-server
`````

`````
mysql // exit
`````

### Instalación de PHP

````
sudo apt install php libapache2-mod-php php-mysql
````

````
php -v
````

### Creación de un Host Virtual para la página

````
mkdir /var/www/your_domain
````

````
chown -R $USER:$USER /var/www/your_domain
````

````
nano /etc/apache2/sites-available/your_domain.conf
````

````
<VirtualHost *:80>
    ServerName your_domain
    ServerAlias www.your_domain
    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/your_domain
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
````

````
a2ensite your_domain
````

````
a2dissite 000-default
````

````
apache2ctl configtest
````

````
systemctl reload apache2
````
````
nano /var/www/your_domain/index.html
````
````
<html>
  <head>
    <title>your_domain website</title>
  </head>
  <body>
    <h1>Hello World!</h1>

    <p>This is the landing page of <strong>your_domain</strong>.</p>
  </body>
</html>
````

````
````
2.
3.