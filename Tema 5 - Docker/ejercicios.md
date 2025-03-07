# Tema 5 Docker (<em>Contenedores en la nube</em>)

## Índice

- [Inicio](../README.md)
- [Tema 0 - Introducción](../Tema%200/Ejercicios.md)
- [Tema 1 - Servidores Web](#Tema-X-Placeholder)
- [Tema 2 - DNS](#Tema-X-Placeholder)
- [Tema 3 - Servidores de Transferencia de archivos](#Tema-X-Placeholder)

- <details><summary>Tema 5 - Docker</summary>

  - [Introducción](#introducción)
  - [Actividad 2](#)
  - [Actividad 3](#)
  - [Actividad 4](#)
  - [Actividad 5](#)

</details>

- [AWS - Amazon Web Services](#Tema-X-Placeholder)

<br>

## Introducción

Plataforma que permite desarrollar, empaquetar y ejecutar aplicaciones en contenedores, proporcionando un entorno portátil y consistente. A diferencia de las máquinas virtuales, los contenedores comparten el kernel del sistema operativo, lo que optimiza el uso de recursos y mejora la eficiencia.  

Su uso simplifica el despliegue de aplicaciones al evitar problemas de compatibilidad entre entornos y facilita la escalabilidad. En esta guía, exploraremos las bases de Docker, haciendo gestión de contenedores e imágenes.

<img src="./img/banner.png" width="1280">

## Actividad 2

### Get-Started - Articulo 1

#### Ejecutar la imagen hello-world

Comenzamos con la ejecución de una imagen de Docker. Para ello, debemos tener instalado Docker en nuestro sistema. Una vez instalado , podemos ejecutar la siguiente orden en la terminal:

````
sudo docker run hello-world
````

<img src="./img/helloworld2.png" width="680">

#### Imagenes locales

Para comprobar las imagenes locales en Docker , podemos utilizar la siguiente orden:

````
sudo docker images -a
````

<img src="./img/images.png" width="680">

#### Mostrar todos los contenedores Docker

En caso de que queramos ver todos los contenedores que se han ejecutado en nuestro sistema, podemos utilizar la siguiente orden:

````
sudo docker ps -a
````

<img src="./img/containers.png" width="680">



### Get-Started Part 2 - Articulo 2

#### Editar el archivo DockerFile

Un Dockerfile es un archivo de texto que contiene un conjunto de instrucciones para construir una imagen de Docker de manera automatizada. Permite definir el entorno, las dependencias y la configuración necesaria para ejecutar una aplicación dentro de un contenedor.

Para editar el archivo Dockerfile, podemos utilizar cualquier editor de texto, aqui emplearemos <em>nano</em> con el siguiente comando:

````
sudo nano RUTA/Dockerfile
````

<img src="./img/dockerfile.png" width="380">

#### Construir el contenedor

Si queremos construir nuestro primer contenedor, podemos utilizar la siguiente orden:

````
sudo docker build -t NOMBRE-IMAGEN .
````

<img src="./img/build.png" width="680">

#### Ejecutar el contenedor

La ejecución de nuestro contenedor se puede realizar con la siguiente orden:

````
sudo docker run -d -p 127.0.0.1:3000 getting-started
````

<img src="./img/startapp.png" width="680">

#### Publicar la imagen en Docker Hub

Para publicar nuestra imagen en Docker Hub, debemos primero crear una cuenta en el sitio web de Docker Hub.

<img src="./img/share1.png" width="680">

Una vez que tengamos una cuenta, debemos iniciar sesión en la consola con el siguiente comando:

````
sudo docker login -u NombreUsuario
````

<img src="./img/share3.png" width="680">

Con todo ello , ya podemos publicar nuestra imagen en Docker Hub con el siguiente comando:

````
sudo docker push davidfau/gettingstarted
````

<img src="./img/share4.png" width="680">

## Actividad 3

## Actividad 4

## Actividad 5