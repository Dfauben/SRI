# AWS (<em>Amazon Web Services</em>)

## Índice

- [Inicio](../README.md)
- [Tema 0 - Introducción](../Tema%200/Ejercicios.md)
- [Tema 1 - Servidores Web](#Tema-X-Placeholder)
- [Tema 2 - DNS](#Tema-X-Placeholder)
- [Tema 3 - Servidores de Transferencia de archivos](#Tema-X-Placeholder)

- <details><summary>Tema 4 - Docker</summary>

  - [Introducción](#introducción)
  - [Actividad 2](#)

</details>

- [AWS - Amazon Web Services](#Tema-X-Placeholder)

<br>

## Introducción



<img src="./img/banner.png" width="1280">

## Actividad 2

### Articulo 1

#### Ejecutar la imagen hello-world

````
sudo docker run hello-world
````

<img src="./img/helloworld2.png" width="680">

#### Imagenes locales

````
sudo docker images -a
````

<img src="./img/images.png" width="680">

#### Mostrar todos los contenedores Docker

````
sudo docker ps -a
````

<img src="./img/containers.png" width="680">



### Articulo 2

#### Editar el archivo DockerFile

````
sudo nano RUTA/Dockerfile
````

<img src="./img/dockerfile.png" width="380">

#### Construir el contenedor

````
sudo docker build -t NOMBRE-IMAGEN .
````

<img src="./img/build.png" width="680">

#### Ejecutar el contenedor

````
sudo docker run -d -p 127.0.0.1:3000 getting-started
````

<img src="./img/startapp.png" width="680">

#### Publicar la imagen en Docker Hub

dwd

<img src="./img/share1.png" width="680">

````
sudo docker login -u NombreUsuario
````

<img src="./img/share3.png" width="680">

````
sudo docker push davidfau/gettingstarted
````

<img src="./img/share4.png" width="680">