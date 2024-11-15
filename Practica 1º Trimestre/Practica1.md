# Práctica Servidores Web - 1º Trimestre

## Indice

- [Inicio ](../README.md)
- [Tema 0 - Introducción ](../../SREI/Tema%200/Ejercicios.md/)
- [Tema 1 - Servidores Web ](../../SREI/Tema%201/Ejercicios.md)
- [Tema 2 - Placeholder ](#Tema-X-Placeholder)
- [Tema 3 - Placeholder ](#Tema-X-Placeholder)
- [Prácticas ](contenidos.md)
    - [1º Trimestre - Servidores Web ](Practica1.md)

## Instalación del servidor web Apache

### Instalación de Apache en Ubuntu

1. Abrimos una terminal

2. Actualizamos los paquetes instalados
`````
sudo apt update
`````
3. Instalamos las nuevas versiones
````
sudo apt upgrade
````
4. Instalamos el paquete de Apache
`````
sudo apt install apache2
`````
5. Ajustamos el Firewall para Apache con los siguientes dos comandos:
`````
sudo ufw app list
`````
`````
sudo ufw allow "Apache"
`````
6. Comprobar en nuestro navegador la siguiente dirección
````
https://localhost
````
Si hemos seguido los pasos habremos instalado correctamente Apache2 para Ubuntu
<br>

<img src="../Tema 1/rsc/img/apachecinstall1.png" alt="index" width="570"/>

<br>


## Activación de los módulos necesarios para PhP y MySQL

### Instalación de MySQL

1. Instalamos MySQL-server

`````
apt install mysql-server
`````
2. Comprobamos, entrando a MySQL con el siguiente comando:
`````
sudo mysql 
`````
3. Para salir de MySQL:
`````
exit
`````
<br>

## Instalación y configuración Wordpress

### Instalamos las dependencias para Wordpress

Ejecutamos los siguientes comandos:

`````
sudo apt install ghostscript
sudo apt install libapache2-mod-php
sudo apt install mysql-server
sudo apt install php
sudo apt install php-bcmath
sudo apt install curl
sudo apt install php-intl
sudo apt install php-json
sudo apt install php-mbstring
sudo apt install php-mysql
sudo apt install php-xml
sudo apt install php-zip
`````

### Instalamos Wordpress

1. Creamos la carpteta contenedora para Wordpress

````
sudo mkdir -p /srv/www
````

2. Cambiamos los permisos de la carpeta

````
sudo chown www-data: /srv/www
````
3. Descargamos los datos necesarios para Wordpress en dicha carpeta

````
sudo curl https://wordpress.org/latest.tar.gz | sudo -u www-data tar zx -C /srv/www 
````

<br>

<img src="../Practica 1º Trimestre/rsc/img/Captura de pantalla 2024-11-15 160333.png" alt="index" width="570"/>

<br>

### Creación y modificación de un archivo de congifuración para Wordpress

1. Creamos el archivo de configuración

````
sudo nano /etc/apache2/sites-available/wordpress.conf
````
2. Editamos con lo siguiente:

````
<VirtualHost *:80>
    DocumentRoot /srv/www/wordpress
    ServerName Wordpress.local
    <Directory /srv/www/wordpress>
        Options FollowSymLinks
        AllowOverride Limit Options FileInfo
        DirectoryIndex index.php
        Require all granted
    </Directory>
    <Directory /srv/www/wordpress/wp-content>
        Options FollowSymLinks
        Require all granted
    </Directory>
</VirtualHost>
````

<br>

3. Habilitamos la página de Wordpress

<br>

````
sudo a2ensite wordpress
````

<br>

4. Deshabilitamos la página por defecto de Apache

<br>

````
sudo a2dissite 000-default
````

<br>

5. Añadimos el dominio al fichero hosts

<br>

````
sudo nano /etc/
````

<br>

6. Recargamos Apache

<br>

````
sudo service Apache2 reload
````

<img src="../Practica 1º Trimestre/rsc/img/wordpress2.png" alt="index" width="570"/>

<br>

### Configuración de la base de datos

````
sudo mysql -u root
````
````
CREATE DATABASE wordpress;
````
````
CREATE USER wordpress@localhost  IDENTIFIED  BY 'Contraseña';
````
````
GRANT SELECT, INSTERT, UPDATE, DELETE, CREATE, DROP, ALTER
    -> ON wordpress.*
    -> TO wordpress@localhost;
````
````
FLUSH PRIVILEGES;
````
````
quit
````
<img src="../Practica 1º Trimestre/rsc/img/database.png" alt="index" width="570"/>

### Configurar la conexión entre Wordpress y la base de datos

````
sudo -u www-data cp /srv/www/wordpress/wp-config-sample.php /srv/www/wordpress/wp-config.php
````

````
sudo -u www-data sed -i 's/database_here/wordpress/'  /srv/www/wordpress/wp-config.php
sudo -u www-data sed -i 's/username_here/wordpress/'  /srv/www/wordpress/wp-config.php
sudo -u www-data sed -i 's/password_here/usuario/'  /srv/www/wordpress/wp-config.php
````

````
sudo -u www-data nano /srv/www/wordpress/wp-config.php
````

````
define( 'AUTH_KEY',         'put your unique phrase here' );
define( 'SECURE_AUTH_KEY',  'put your unique phrase here' );
define( 'LOGGED_IN_KEY',    'put your unique phrase here' );
define( 'NONCE_KEY',        'put your unique phrase here' );
define( 'AUTH_SALT',        'put your unique phrase here' );
define( 'SECURE_AUTH_SALT', 'put your unique phrase here' );
define( 'LOGGED_IN_SALT',   'put your unique phrase here' );
define( 'NONCE_SALT',       'put your unique phrase here' );
````


## Activación del módulo 'WSGI' para apliaciones Python

## Utilizando aplicaciones Python

## Medidas de seguridad en el acceso: Autenticación

## Instalación y configuración de AWSTAT

## Instalación de un segundo servidor
