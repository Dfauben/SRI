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
sudo apt install mysql-server
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
sudo install php
`````

### Instalamos Wordpress

1. Creamos la carpteta contenedora para Wordpress

````
sudo mkdir -p /var/www/html
````

2. Cambiamos los permisos de la carpeta

````
sudo chown www-data: /var/www/html
````
3. Descargamos los datos necesarios para Wordpress en dicha carpeta

````

````


<br>

<br>

### Creación y modificación de un archivo de configuración para Wordpress

1. Creamos el archivo de configuración

````
sudo nano /etc/apache2/sites-available/wordpress.conf
````
2. Editamos con lo siguiente:

````
<VirtualHost *:80>
    DocumentRoot /var/www/html
    ServerName wordpress.local
    ServerAdmin admin@localhost
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
sudo nano /etc/hosts
````

<img src="../Practica 1º Trimestre/rsc/img/hosts.png" alt="index" width="570"/>


<br>

6. Recargamos Apache

<br>

````
sudo service Apache2 reload
````

<br>

### Configuración de la base de datos
<br>

Accedemos a MySQL como administradrores

````
sudo mysql -u root
````
<br>

Creamos nuestra base datos, en este caso el nombre será wordpress
````
CREATE DATABASE wordpress;
````
<br>
Creamos un usuario admin para MySQL 

````
CREATE USER 'admin'@'localhost'  IDENTIFIED  BY 'admin';
````
<br>
Otorgamos todos los privilegios al usuario admin

````
GRANT ALL PRIVILEGES -> ON wordpress.* -> TO 'admin'@'localhost';
````
<br>
Actualizamos los privilegios de nuestra base de datos

````
FLUSH PRIVILEGES;
````
<br>
Cerramos la sesión de MySQL

````
quit
````
<br>

<img src="../Practica 1º Trimestre/rsc/img/database.png" alt="index" width="570"/>

<br>

### Configurar la conexión entre Wordpress y la base de datos

<br>
Copiamos la 

````
sudo -u www-data cp /var/www/html/wp-config-sample.php /var/www/html/wp-config.php
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

### Configuración de Wordpress

Ingresamos a nuestro dominio y comenzamos la configuración básica de Wordpress.
Seleccionamos el idioma.

<img src="../Practica 1º Trimestre/rsc/img/wordpress.png" alt="index" width="570"/>

Continuamos con la configuración, añadimos nombre a nuestro sitio, correo electrónico y contraseña de administrador.

<img src="../Practica 1º Trimestre/rsc/img/wordpress3.png" alt="index" width="570"/>

Habremos finalizado la configuración básica de Wordpress.

<img src="../Practica 1º Trimestre/rsc/img/wordpress4.png" alt="index" width="570"/>

Accedemos a la página de inicio de Wordpress e ingresamos con nuestras credenciales.

<img src="../Practica 1º Trimestre/rsc/img/wordpress5.png" alt="index" width="570"/>

Finalmente comprobamos el correcto funcionamiento de Wordpress.

<img src="../Practica 1º Trimestre/rsc/img/wordpress6.png" alt="index" width="570"/>

<br>

## Activación del módulo 'WSGI' para apliaciones Python

## Utilizando aplicaciones Python

## Medidas de seguridad en el acceso: Autenticación

## Instalación y configuración de AWSTAT

## Instalación de un segundo servidor
