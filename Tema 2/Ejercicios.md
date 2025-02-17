# Tema 2 - DNS (<em>Domain Name System</em>)

## Indice

- [Inicio](../README.md)
- [Tema 0 - Introducción](../Tema%200/Ejercicios.md)

- <details><summary>Tema 1 - Servidores Web</summary>

  <details>
  <summary>Actividad #1 - Instalación del servidor web</summary>

  - [Instalación de Apache](#instalación-de-apache-en-ubuntu)
  - [Instalación de MySQL](#instalación-de-mysql)
  - [Instalación de PHP](#instalación-de-php)
  - [Creación de un Host Virtual para la página](#creación-de-un-host-virtual-para-la-página)

  </details>

  <details><summary>Actividad #2 - Configuración básica de Apache (Scripts)</summary>

  - [Script #1](#1-creación-de-un-script-que-añada-un-puerto-de-escucha-en-el-fichero-de-configuración-de-apache)
  - [Script #2](#2-creación-de-un-script-que-añada-un-nombre-de-dominio-y-una-ip-en-el-fichero-hosts)
  - [Script #3](#3-crea-un-script-que-nos-permita-crear-una-página-web-con-un-título-una-cabecera-y-un-mensaje)

  </details>

  <details>
  <summary>Actividad #7 - Módulo Rewrite</summary>

  - [Habilitar Móddulo](#habilitando-el-módulo-rewrite)
  - [Creación de un .htacces](#crear-un-htacces-para-rewrite)
  - [Redirección con cambio de extensión](#redirección-url-con-diferente-extensión) 
  - [URL amigable](#url-amigable)
  - [Redirección a página externa](#redireccionar-a-una-página-externa)
  - [Redirección según navegador](#redireccionar-según-el-navegador-utilizado)

  </details>

  <details>
  <summary>Actividad #9 - Autenticación y Autorización</summary>

  - [Creación de usuarios](#creación-de-usuarios)
  - [Crear grupos de usuarios](#crear-grupos-de-usuarios)
  - [Directorios Privados](#directorios-privados)
  - [Directiva Satisfy](#directiva-satisfy)
  - [Restricción de acceso local](#restricción-de-acceso-local)
  - [Autenticación con MySQL](#autenticación-mysql)


  </details>

  <details>
  <summary>Actividad #10 - Crear un certificado autofirmado y activar el módulo SSL</summary>

  - [Módulo SSL](#actividad-10---crear-un-certificado-autofirmado-y-activar-el-módulo-ssl)

  </details>

</details>

- [Tema 2 - Placeholder](#Tema-X-Placeholder)
- [Tema 3 - Placeholder](#Tema-X-Placeholder)

<br>

## Actividad #2 - NsLookup

### Ejercicio 1

#### La UHU (Universidad de Huelva) tiene varios servidores DNS. Consulta a tu servidor DNS por defecto sus direcciones IP al menos 2 de ellos.

Utilizamos el comando:

````
nslookup -type=ns uhu.es
````

Con el que obtendremos la lista de servidores DNS asociados al dominio que consultemos.

<img src="./img/nslookup.png">

<br>

Luego emplearemos el comando con el que obtendremos la IP:

````
nslookup 'nombre del servidor DNS'
````

<img src="./img/nslookup1.png">

<img src="./img/nslookup1_2.png">

<br>

### Actividad #2

#### ¿Son las respuestas anteriores autoritativas? 

Al no venir de un servidor autoritativo, la información no es fiable, por lo tanto no es autoritativa.

<br>

### Actividad #3

#### Consulta la dirección IP de un servidor de correo de uhu.es.

Utilizamos el comando:

````
nslookup -type=mx uhu.es dns.uhu.es
````

Con el que obtendremos la IP del servidor de correo asociado al dominio que consultemos.

<img src="./img/nslookup3.png">

<br>

### Actividad #4

#### ¿Son las respuestas anteriores autoritativas? 

Sí, ya que comprobamos que la informción solicitada proviene de un servidor autoritativo del dominio.

<br>

### Actividad #5

#### Si hay más de un servidor dns autoritativo para el dominio uhu.es, ¿cómo sabemos cuál es el primario? ¿en qué fecha se actualizó por última vez? ¿cúal es la dirección e-mail del administrador?

Utilizamos el siguiente comando:

````
nslookup -type=soa uhu.es dns-1.uhu.es
````

<img src="./img/nslookup5.png">

Del que obtenemos:

Servidor primario: <b>master.infoblox</b><br>
Última fecha de actualización: <b>Hace 4 horas</b><br>
La dirección e-mail del administrador la encontramos en: <b>responsible mail addr</b><br>

Aunque observamos que no se encuentra definida.

<br>

### Actividad #6

#### Comprueba que el DNS inverso está bien configurado para dns-1.uhu.es.

Consultamos la dirección IP del servidor dns-1.uhu.es con el siguiente comando:
````
nslookup dns-1.uhu.es
````
<img src="./img/nslookup6.png">

<br>

Obtenemos que la dirección IP es 150.214.167.1.
Ahora realizamos el DNS inverso con el siguiente comando:

````
nslookup 150.214.167.1
````

<img src="./img/nslookup6_1.png">

Comprobamos que la busqueda nos devuelve el nombre del servidor dns-1.uhu.es. Por lo tanto, el DNS inverso está bien configurado.

<br>

### Actividad #7

#### Comprueba que el DNS inverso está bien configurado para www.bp.com.

Consultamos la dirección IP del dominio www.bp.com con el siguiente comando:
````
nslookup bp.com
````

<img src="./img/nslookup7.png">

<br>

Obtenemos que la dirección IP es 54.72.215.189
Ahora realizamos el DNS inverso con el siguiente comando:

````
nslookup 54.72.215.189
````

<img src="./img/nslookup7_1.png">

<br>

### Actividad #8

#### Por defecto, el comando NSLOOKUP devuelve los registros de tipo A. ¿Qué se obtiene al consultar los registros NS? Se obtienen los servidores autoritativos para un dominio.

Para consultar los registros de tipo ns, añadimos a nuestro comando el parámetro -type=ns. Utilizamos el comando:

````
nslookup -type=ns Nombre_Dominio
````

Con <b>-type=ns</b> obtendremos los nombres de los servidores DNS autoritaticos asociados al dominio que estamos consultando.

<br>

### Actividad #9

#### Consulta el TLD de las páginas de España: “es”.

Empleamos el siguiente comando:

````
nslookup -type=ns es
````

<img src="./img/nslookup9.png">

<br>

### Actividad #10

#### ¿Puede un mismo nombre de dominio traducirse en varias direcciones IP distintas? 

Sí, en la mayoría de caso se desea una alta disponibilidad, por ello un mismo dominio tiene varios servidores de respaldo, lo que se traduce como que un mismo dominio tenga varias IP.

### Actividad #11

#### ¿Quién decide a cuál de las direcciones IP se envía una petición? 

El <em>DNS resolver local</em> es quien se encargará de decidir a cuál de las direcciones IP se envía una petición. El DNS resolver procesará la solicitud y se encargará de dar la dirección IP correcta.

## Ejercicio de 6 - Master DNS

### Configuración de Zona DNS

Editamos el archivo hosts con el siguiente comando:

````
sudo nano /etc/hosts
````

Mantenemos actualizados los paquetes de Ubuntu con los siguientes comandos:

````
sudo apt update
sudo apt upgrade -y
````

Instalamos BIND:
````
sudo apt install bind9 bind9utils bind9-doc -y
````

