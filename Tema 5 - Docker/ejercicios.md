# Tema 5 Docker (<em>Contenedores en la nube</em>)

## Índice

- [Inicio](../README.md)
- [Introducción](../Tema%200/Ejercicios.md)
- [Servidores Web](../Tema%201/Ejercicios.md)
- [Domain Name System (DNS)](../Tema%202/Ejercicios.md)

- <details><summary>Docker</summary>

  - [Introducción](#introducción)
  - [Actividad 2](#)
  - [Actividad 3](#)
  - [Actividad 4](#)
  - [Actividad 5](#)

</details>

- [AWS - Amazon Web Services](../Tema%204%20AWS/Ejercicios.md)

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

---

### 1. Descargar imágenes de Docker
Ejecuta los siguientes comandos para descargar las imágenes necesarias:

```sh
docker pull ubuntu
docker pull hello-world
docker pull nginx
```

<img src="./img/pull.png" width="680">

Para verificar que las imágenes se han descargado correctamente, usa:

```sh
docker images -a
```

<img src="./img/check.png" width="680">

---

### 2. Ejecutar contenedores
Lanza tres contenedores basados en la imagen `hello-world` con nombres específicos:

```sh
docker run --name myhello1 hello-world
docker run --name myhello2 hello-world
docker run --name myhello3 hello-world
```

<img src="./img/helloworld1_1.png" width="680">

ℹ️ **Nota:** `hello-world` es una imagen de prueba que se ejecuta y finaliza inmediatamente.
Para ver la lista de contenedores creados (ejecutados o detenidos), usa:

```sh
docker ps -a
```

---

## 3. Mostrar contenedores en ejecución
Para listar solo los contenedores en ejecución:

```sh
docker ps
```

<img src="./img/check2.png" width="680">

---

## 4. Detener contenedores
Si algún contenedor sigue en ejecución, puedes detenerlo con:

```sh
docker stop myhello1
docker stop myhello2
```

<img src="./img/stop.png" width="680">

---

## 5. Eliminar contenedores
Para eliminar un contenedor específico:

```sh
docker rm myhello1
```

<img src="./img/rm.png" width="680">


Para verificar los contenedores después de eliminar uno:

```sh
docker ps -a
```

Para eliminar **todos los contenedores**, ejecuta:

```sh
docker ps -aq | xargs docker rm
```

<img src="./img/rmall.png" width="680">


⚠️ **Precaución:** Este comando elimina **todos** los contenedores, incluso los detenidos.

---

## Actividad 4



## Actividad 5