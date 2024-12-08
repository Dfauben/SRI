# Práctica Servidores Web - 1º Trimestre


<img src="../Practica 1º Trimestre/rsc/img/icon.png" alt="index" width="550"/>

## Indice

- [Inicio ](../README.md)
- [Tema 0 - Introducción ](../../SREI/Tema%200/Ejercicios.md/)
- [Tema 1 - Servidores Web ](../../SREI/Tema%201/Ejercicios.md)
- [Tema 2 - Placeholder ](#Tema-X-Placeholder)
- [Tema 3 - Placeholder ](#Tema-X-Placeholder)
- <details><summary>Trabajos prácticos</summary>

    <details><summary>Servidores Web</summary>

    - [Instalación del servidor web Apache](#instalación-del-servidor-web-apache)
    - [Instalación de MySQL](#instalación-de-mysql)

        <details><summary>Instalación y configuración Wordpress</summary>

        - [Instalamos las dependencias para Wordpress](#instalamos-las-dependencias-para-wordpress)
        - [Instalación de Wordpress](#instalamos-wordpress)
        - [Creación y modificación de un archivo de configuración para Wordpress](#creación-y-modificación-de-un-archivo-de-configuración-para-wordpress)
        - [Configuración de la base de datos](#configuración-de-la-base-de-datos)
        - [Configurar la conexión entre Wordpress y la base de datos](#configurar-la-conexión-entre-wordpress-y-la-base-de-datos)

        </details>

        <details>
        <summary>Módulo 'WSGI' para aplicaciones Python</summary>

        - [Activación del módulo 'WSGI' para aplicaciones Python](#activación-del-módulo-wsgi-para-aplicaciones-python)
        - [Utilizando aplicaciones Python](#utilizando-aplicaciones-python)
        - [Medidas de seguridad al acceso de la aplicación Python](#medidas-de-seguridad-al-acceso-de-la-aplicación-python)

        </details>

    - [Instalación y configuración de AWSTAT](#instalación-y-configuración-de-awstat)

        <details>
        <summary>Segundo servidor web con Nginx</summary>

        - [Instalación de Nginx](#instalación-de-un-segundo-servidor)
        - [Instalacion MySQL](#instalación-mysql)
        - [Instalación PHP y dependencias](#instalación-php)
        - [Instalación phpMyAdmin](#instalación-phpmyadmin)


        </details>
    </details>

</details>


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
sudo apt install -y php8.1-cli php8.1-fpm php8.1-mysql
`````

### Instalamos Wordpress

1. Descargamos el archivo de instalación de Wordpress:

````
wget https://es.wordpress.org/latest.zip
````

2. Extraemos los archivos

````
sudo unzip latest.zip
````

Si necesitamos el comando unzip lo podemos instalar con el siguiente comando:

````
sudo apt install unzip
````

3. Movemos los contenidos de Wordpress a la carpeta del dominio

````
sudo mv wordpress/* /var/www/html/
````

4. Cambiamos los permisos de la carpeta

````
sudo chown -R www-data:www-data /var/www/html/*
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

Copiamos la configuracion por defecto de wordpress en el archivo wp-config-sample.php a wp-config.php

````
sudo -u www-data cp /var/www/html/wp-config-sample.php /var/www/html/wp-config.php
````

Modificamos el archivo de configuración de WordPress para que se conecte a la base de datos que creamos anteriormente.

````
sudo -u www-data nano /srv/www/wordpress/wp-config.php
````

Dentro del documento , debemos cambiar los siguientes valores por aquellos que definimos en nuestra base de datos:

````
define( 'DB_NAME',          'Nombre_Base_Datos' );
define( 'DB_USER',          'Nombre_Usuario' );
define( 'DB_PASSWORD',      'Contraseña' );
````

<br>
<br>

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

## Activación del módulo 'WSGI' para aplicaciones Python

1. Instalamos Python:
````
sudo apt install python3 libexpat1 -y
````

2. Instalamos el módulo WSGI
````
sudo apt install libapache2-mod-wsgi-py3 -y
````

<br>
<br>

## Utilizando aplicaciones Python

1. Probamos el módulo con un script de prueba:

````
sudo nano /var/www/html/wsgi_test.py
````

2. Agregamos el siguiente código al archivo wsgi_test.py:
````Python
def application(environ, start_response):
    status = '200 OK'
    output = b'Hello !\n'

    response_headers = [
        ('Content-type', 'text/plain'),
        ('Content-Length', str(len(output)))
    ]

    start_response(status, response_headers)
    return [output]
````

3. Cambiamos el dueño y permisos del archivo

````
sudo chown www-data:www-data /var/www/html/wsgitest.py
sudo chmod 775 /var/www/html/wsgitest.py
````

4. En el archivo de configuración de nuestro VirtualHost añadimos:
````
WSGIScriptAlias / /var/www/html/wsgitest.py
````

5.  Ingresamos al dominio añadiendo al  final /wsgi

<img src="../Practica 1º Trimestre/rsc/img/pyrhon.png" alt="index" width="570"/>

<br>
<br>

## Medidas de seguridad al acceso de la aplicación Python

1. Utilizaremos el módulo auth_basic, para empezar a utilizar este módulo debemos habilitarlo, primero para ello escribimos en una terminal lo siguiente:
````
sudo a2enmod auth_basic
````

2. Definimos primero un archivo donde se almacene la información relativa de los usuarios, entonces desde una terminal escribimos:

````
sudo htpasswd -c /etc/apache2/.htpasswd usuario
````

3. Ingresamos al archivo de configuración del VirtualHost:
````
sudo nano /etc/apache2/sites-available/nombre-dominio.conf
````

4. Agregamos la siguiente línea al archivo de configuración:
````
<Location /wsgi>
  AuthType Basic
  AuthName "Nombre_Opcional"
  AuthUserFile /etc/apache2/.htpsswd
  Require valid-user
</Location>
````

5. Comprobamos que no podemos acceder al módulo WSGI

<img src="../Practica 1º Trimestre/rsc/img/auth.png" alt="index" width="570"/>

<br>
<br>

## Instalación y configuración de AWSTAT

1. Instalamos AWSTAT mediante el siguiente comando:
````
sudo apt-get install awstats
````

<br>

2. Habilitamos el módulo CGI:
````
sudo a2enmod cgi alias
````

<br>

3. Reiniciamos Apache:
````
sudo service apache2 restart
````

<br>

4. Duplicamos el archivo de configuración de AWSTAT:
````
sudo cp /etc/awstats/awstats.conf /etc/awstats/awstats.Nombre-Dominio.conf
````

<br>

5. Editamos el archivo de configuración de AWSTAT:
````
sudo nano /etc/awstats/awstats.Nombre-Dominio.conf
````
````
LogFile="/var/log/apache2/access.log"
SiteDomain="Dominio.com"
HostAliases="www.Dominio.com localhost 127.0.0.1"
````

<br>

6. Generamos estadisticas de AWSTAT:

````
sudo /usr/lib/cgi-bin/awstats.pl -config=Nombre-Dominio -update
````

<br>

7. Cambiamos los permisos del log generado:
````
sudo chmod o+r /var/log/apache2/acces.log
````

<br>

8. Generamos un index para nuestra pagina de estadisticas AWSTATS:
````
sudo /usr/lib/cgi-bin/awstats.pl -config=Dominio.com -output > /var/www/html/index.html
````

<br>

9. Visualizamos en el navegador

<img src="../Practica 1º Trimestre/rsc/img/awstats.png" alt="index" width="570"/>

<br>
<br>

## Instalación de un segundo servidor

1. Instalamos Nginx
````
sudo apt-get install nginx
````

2. Ajustamos el firewall
````
sudo ufw allow 'Nginx HTTP'
````

3. Comprobamos que funciona

<img src="../Practica 1º Trimestre/rsc/img/nginx.png" alt="index" width="570"/>

4. Creamos una carpeta para el sitio web

````
sudo mkdir /var/www/server2
````

5. Creamos el archivo de configuracion del dominio
````
sudo nano /etc/nginx/sites-available/servidor2.centro.intranet
````

6. Agregamos lo siguiente:
````
server {
    listen 8080;
    server_name servidor2.centro.intranet;

    root /var/www/servidor2.centro.intranet;
    index index.php index.html index.htm;

    location / {
        try_files $uri $uri/ =404;
    }

    location /phpmyadmin {
        root /var/www/html;
        index index.php;
        try_files $uri $uri/ =404;

        location ~ \.php$ {
            include snippets/fastcgi-php.conf;
            fastcgi_pass unix:/var/run/php/php8.1-fpm.sock; # Ajusta según tu versión de PHP
            fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
            include fastcgi_params;
        }
    }

    location ~ /\.ht {
        deny all;
    }
}

````

7. Configuramos el archivo hosts:
````
111.111.111.111 servidor2.centro.intranet
````

7. Habilitamos el sitio web
````
sudo ln -s /etc/nginx/sites-available/servidor2.centro.intranet /etc/nginx/sites-enabled/
````

8. Reiniciamos el servicio de Nginx
````
sudo service nginx restart
````

9. Comprobamos que funciona

<img src="../Practica 1º Trimestre/rsc/img/nginxprueba.png" alt="index" width="570"/>

<br>

### Instalación MySQL

1.  Instalamos MySQL
````
sudo apt-get install mysql-server -y
````

2. Configuramos MySQLServer:

````
sudo mysql_secure_installation
````

<img src="../Practica 1º Trimestre/rsc/img/sql.png" alt="index" width="570"/>

3. Creamos el usuario phpmyadmin para la posterior instalación de phpmyadmin:

````
sudo mysql -u root -p
````
````
CREATE USER 'phpmyadmin'@'localhost' IDENTIFIED BY 'Contraseña';
GRANT ALL PRIVILEGES ON *.* TO 'phpmyadmin'@'localhost' WITH GRANT OPTION;
FLUSH PRIVILEGES;
EXIT;
````

<br>
<br>

### Instalación PHP

1. Instalamos PHP y sus dependencias:
````
sudo apt install php-fpm php-mysql php-mbstring php-zip php-gd php-json php-curl -y
````

2. Configurar PHP-FPM para evitar problemas con Nginx:
````
sudo nano /etc/php/8.1/fpm/php.ini
````
````
cgi.fix_pathinfo=0
````

<img src="../Practica 1º Trimestre/rsc/img/nginx_php.png" alt="index" width="570"/>

3. Reiniciamos el servicio de PHP-FPM:
````
sudo service php8.1-fpm restart
````

<br>
<br>

### Instalación phpMyAdmin

1. Instalamos PHPmyAdmin
````
sudo apt-get install phpmyadmin
````

<br>

2. Configuramos PHPmyAdmin, seleccionamos apache2:

<img src="../Practica 1º Trimestre/rsc/img/nginx3.png" alt="index" width="570"/>

<br>

Posteriormente ingresamos la contraseña que habriamos establecido en el paso de instalación de MySQL

<br>

3. Incluimos en la carpeta de nuestro dominio los archivos de PHPmyAdmin:
````
sudo ln -s /usr/share/phpmyadmin /var/www/server2/
````

<br>

4. Comprobamos que funciona:

<img src="../Practica 1º Trimestre/rsc/img/nginx_phpmyadmin.png" alt="index" width="570"/>

<img src="../Practica 1º Trimestre/rsc/img/nginx_phpmyadmin2.png" alt="index" width="570"/>