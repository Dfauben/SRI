# Tema 1 - Servidores Web

## Indice

- [Inicio ](../README.md)
- [Tema 0 - Introducción ](../Tema%200/Ejercicios.md)
- [Tema 1 - Servidores Web ](#indice)
  - [Actividad #1](#)
    - [Instalación de Apache ](#)
    - [Instalación de MySQL ](#)
    - [Instalación de PHP ](#)
    - [Creación de un Host Virtual para la página](#)
  - [Actividad #2](#)
- [Tema 2 - Placeholder ](#Tema-X-Placeholder)
- [Tema 3 - Placeholder ](#Tema-X-Placeholder)

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

<br>

<img src="./rsc/img/index.png" alt="index" width="470"/>

<br>

### Probando PHP en el Servidor Web

Vamos a crear un documento PHP de prueba con el que confirmar que PHP se encuentra instalado y en funcionamiento, para ello escribimos el siguiente comando en la terminal de Linux.

````
nano /var/www/Nombre_Dominio/info.php
````

Ahora con el editor de texto abierto, creamos las siguientes líneas dentro del documento:

````
<?php
phpinfo();
````

Finalmente guardamos los cambios del documento con **CTRL + O** y lo cerramos con **CTRL + X**. Ahora simplemento añadimos a nuestra URL habitual el sufijo ***/info.php***, quedaría nuestra URL de la siguiente forma:

````
localhost/info.php
````

<br>

<img src="./rsc/img/phpinfo.png" alt="phpinfo" width="470"/>