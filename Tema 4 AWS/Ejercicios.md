# AWS (<em>Amazon Web Services</em>)

## Índice

- [Inicio](../README.md)
- [Tema 0 - Introducción](../Tema%200/Ejercicios.md)
- [Tema 1 - Servidores Web](#Tema-X-Placeholder)
- [Tema 2 - DNS](#Tema-X-Placeholder)

- <details><summary>AWS - Amazon Web Services</summary>

  - [Introducción](#introducción)
  - [Creación de instancias](#creación-de-instancias)
  - [Apache y PHP](#apache-y-php)
  - [Creación de la base de datos](#creación-de-la-base-de-datos)
  - [Elastic File System (EFS)](#elastic-file-system-efs)
  - [Descarga de Wordpress](#descarga-de-wordpress)

</details>

- [Tema 3 - Placeholder](#Tema-X-Placeholder)

<br>

## Introducción

<em>Amazon Web Services</em> (AWS) es una plataforma de computación en la nube que ofrece una amplia variedad de servicios para el almacenamiento, procesamiento, redes y bases de datos. Es utilizada por empresas y desarrolladores para desplegar aplicaciones escalables y seguras sin necesidad de administrar infraestructura física.

<img src="./img/banner.png" width="1280">

## Creación de instancias
La creación de instancias en AWS se realiza a través del servicio Amazon Elastic Compute Cloud, conocido como EC2. Permite lanzar y gestionar máquinas virtuales configurando el sistema operativo, el tipo de instancia y los permisos de acceso. Tras su creación, es posible conectarse a la instancia y configurarla según las necesidades del usuario.

Antes de crear nuestra instancia, deberemos establecer una <em>Virtual Private Cloud</em> (VPC) con la que trabajaremos . Una VPC es una red virtual privada que nos permite configurar subredes, direcciones IP y seguridad para nuestras instancias. Además , debemos crear un Grupo de Seguridad que nos permita configurar las reglas de acceso a nuestra instancia.

### Grupos de Seguridad
Creamos nuestro grupo de seguridad dejando abierto los puertos 80, 22 y 443, asignamos el grupo en nuestra VPC. 
<br></br>
<img src="./img/Seguridad.png" width="470">

### Configuración de la instancia
Lanzamos una instancia con Ubuntu server
<br></br>
<img src="./img/instancia.png" width="870">

#### Asignación del grupo de seguridad a nuestra instancia
Vamos a la pestaña de Configuraciones de red, editamos la configuración de red y seleccionamos el grupo de seguridad que creamos anteriormente. También asignaremos nuestra VPC.
<br></br>
<img src="./img/vpc.png" width="870">

Finalmente entramos en nuestra máquina sin problemas.
<br></br>
<img src="./img/pas1.png" width="470">

## Apache y PHP
Para servir aplicaciones web en AWS, se puede instalar un servidor Apache junto con PHP en una instancia EC2. Apache es un servidor web ampliamente utilizado, y PHP es un lenguaje de programación para el desarrollo de aplicaciones dinámicas. Tras la instalación, se pueden crear archivos PHP y verificar su correcto funcionamiento a través del navegador.

### Instalación 

#### Apache
Actualizamos los paquetes de Ubuntu y luego instalamos Apache y PHP. Para ello haremos un comando <em>update</em> y posteriormete <em>upgrade</em> con los comandos:
````
sudo apt update
sudo apt upgrade
````
Luego instalamos Apache con los siguientes comandos:
````
sudo apt install apache2
````
Para arrcancar el servidor utilizamos el comando:
````
sudo systemctl start apache2
````
Y para habilitar el arranque cada vez que la instancia se inicie:
````
sudo systemctl enable apache2
````
<br>
Vemos que Apache está funcionando correctamente.
<br></br>
<img src="./img/apachestatus.png" width="570">

#### PHP
Instalamos PHP con el comando:
````
sudo apt install php8.2 libapache2-mod-php8.2 php8.2-cli
````
También instalaremos MySQL para la base de datos:
````
sudo apt install php8.2-mysql
````
**NOTA:**<br>
En caso de no poder instalar PHP y sus módulos, ejecutar primero el comando:
````
sudo add-apt-repository ppa:ondrej/php -y
````


<br>
Ahora nos tocará simplemente reiniciar Apache y comprobar que todo está instalado.
Para comprobar que Apache funciona, accedemos a la dirección publica de nuestra instancia.
<br></br>
<img src="./img/apacheweb.png" width="570">

## Creación de la base de datos
AWS ofrece Amazon RDS para gestionar bases de datos en la nube. Al crear una base de datos en este servicio, se elige un motor como MySQL o PostgreSQL, se configuran los recursos asignados y se definen credenciales de acceso. Posteriormente, la base de datos puede ser gestionada y utilizada desde las instancias EC2 o cualquier otro servicio de AWS que la requiera.

#### Base de datos MySQL

Desde la pestaña de RDS en AWS, seleccionamos crear una nueva base de datos, luego seleccionamos MySQL como motor de nuestra base de datos.
<br></br>
<img src="./img/BD1.png" width="870">
<br></br>
Seleccionamos **Capa gratuita**
<br></br>
<img src="./img/BD2.png" width="870">
<br></br>
Configuramos el identficador y las credenciales de la Base de Datos.
<br></br>
<img src="./img/BD3.png" width="870">
<br></br>
Ahora nos toca ajustar las diferentes opciones de conectividad y seguridad. Asignamos nuestra VPC y grupo de seguridad
<br></br>
<img src="./img/BD4.png" width="870">
<br></br>
Finalmente deberemos inevitablemente poner nombre al campo **Nombre de la base de datos incial**
<br></br>
<img src="./img/BD5.png" width="870">
<br></br>
Ahora acudimos al panel de nuestras bases de datos y seleccionamos la base de datos que acabamos de crear clicamos en Acciones y luego en **Configurar la conexión de EC2**, seleccionamos nuestra instancia y damos en **Continuar**.
<br></br>
<img src="./img/BD6.png" width="870">

Comprobamos la conexión de la base de datos desde nuestra instancia EC2. Lo hacemos con el comando:
````
mysql -h puerto_de_enlace_BD -u usuario -p
````
<br>
<img src="./img/BD7.png" width="870">


## Elastic File System (EFS)
<em>Amazon Elastic File System</em> (EFS) permite compartir un sistema de archivos entre varias instancias EC2. Para utilizarlo, se crea un sistema de archivos desde la consola de AWS y se configura su acceso para que pueda ser montado en una instancia. Esto facilita el almacenamiento y acceso a archivos desde múltiples servidores sin necesidad de configuraciones complejas.

Accedemos a la pestaña de EFS en AWS y seleccionamos **Crear sistema de archivos**. Ponemos un nombre y asociamos a nuestra VPC

<img src="./img/EFS1.png" width="670"><br>

Tendremos que crear una nueva regla para nuestro grupo de seguridad que nos permita acceder a nuestro sistema de archivos. Para ello, seleccionamos la pestaña de grupos de seguridad y luego seleccionamos la regla de entrada que queremos modificar. En el campo **Tipo de protocolo**, seleccionamos **NFS**.

<br>
<img src="./img/EFS2.png" width="870">

<br>

Acudimos a la sección de EFS y seleccionamos nuestro EFS, clicamos en **Red** y administramos nuestro punto de montaje. En nuestra subred deberemos proporcionar el grupo de seguridad.

<br>
<img src="./img/EFS5.png" width="870"><br>

Para asociar nuestro EFS a nuestra instancia EC2, debemos montarlo en nuestra instancia. Para ello, ejecutamos el comando que encontramos en el botón de **Asociar** del panel de nuestra EFS.

<br>
<img src="./img/EFS3.png" width="870">

<br>

Vamos a nuestra instancia y con el comando anterior montamos nuestro EFS. Comprobamos su montaje con el comando:
````
df -h
````

<br>
<img src="./img/EFS4.png" width="870">

<br>


## Descarga de Wordpress
Para descargar e instalar WordPress en una instancia EC2, se obtiene el paquete oficial desde su sitio web y se descomprime en el directorio adecuado del servidor web. Posteriormente, se configuran los archivos necesarios para conectar WordPress con la base de datos y completar la instalación a través del navegador. Esto permite desplegar un sitio web funcional en AWS con facilidad.

Descargamos la ultima versión de wordpress dentro de nuestro directorio de apache "/var/www/html" con el comando:
````
sudo wget https://es.wordpress.org/latest.tar.gz
````
Lo descomprimimos con el comando:
````
tar -xf latest.tar.gz
````
<br>
<img src="./img/WP1.png" width="870">

<br>

Volvemos a entrar en MySQL con nuestra credenciales. Necesitaremos tener instalado el cliente de MySQL, lo instalammos con:
````
sudo apt install mysql-client -y
````
<br>
<img src="./img/BD7.png" width="870">

<br>

Ahora crearemos una base de datos con los comandos:
````MySQL
CREATE DATABASE wordpress;
CREATE USER 'wordpress_user'@'%' IDENTIFIED BY 'password123';
GRANT ALL PRIVILEGES ON wordpress.* TO 'wordpress_user'@'%';
FLUSH PRIVILEGES;
````

Entramos desde la ip publica de nuestra instancia desde el navegador

<img src="./img/WP2.png" width="870">

<br>

A continuación deberemos rellenar los campos con el nombre de la base de datos de RDS, el nombre de usuario y contraseña que creamos anteriormente, y el punto de enlace de la base de datos. Una vez rellenados los campos, pulsamos **Submit**.


#### Vinculación del EFS en Wordpress (Carpeta wp-content)

Detenmos primero apache con el comando:

````
sudo systemctl stop apache2
````

Movemos la carpeta **wp-content** a nuestro EFS con el comando:

````
sudo cp -r /var/www/html/wp-content Ruta_EFS
````

Podemos renombrar la carpeta original para que no se sobreescriba con el comando:

````
sudo mv /var/www/html/wp-content /var/www/html/wp-content-old
````

Creamos una vinculación de la carpeta wp-content en el EFS con el comando:

````
sudo ln -s /mnt/efs/wp-content /var/www/html/wp-content
````

Modificamos los permisos de la carpeta EFS para que el usuario apache pueda leer y escribir en ella:

````
sudo chown -R www-data:www-data /mnt/efs/wp-content
sudo chmod -R 775 /mnt/efs/wp-content
````

Finalmente , reiniciamos apache para que se apliquen los cambios:

````
sudo systemctl start apache2
````

<br></br>

**NOTA**:
Para realizar un montaje automatico de EFS tendremos que editar el archivo de configuración **fstab** mediante el comando:
````
sudo nano /etc/fstab
````
E incluir al final lo siguiente:
````
IP_Instancia:/ Ruta_EFS nsf4 default,_netdev 0 0
````

<img src="./img/WP4.png" width="870">

<br>