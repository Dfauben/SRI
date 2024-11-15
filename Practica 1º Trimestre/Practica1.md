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

<img src="../../SREI/Tema 1/rsc/img/apachecinstall1.png" alt="index" width="570"/>

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

## Activación del módulo 'WSGI' para apliaciones Python

## Utilizando aplicaciones Python

## Medidas de seguridad en el acceso: Autenticación

## Instalación y configuración de AWSTAT

## Instalación de un segundo servidor
