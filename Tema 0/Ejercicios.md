# Tema 0 - Introducción a HTTP 

## Indice

- [Inicio ](#Tema-0-Introducción)
- [Tema 0 - Introducción ](#Tema-0-Introducción)
    - [Ejercicio 1 - Introducción ](#Tema-0-Introducción)
    - [Ejercicio 2 - Comparativa entre UDP y TCP](#Tema-0-Introducción)
    - [Ejercicio 3 - Práctica de Telnet/HTTP](#Tema-0-Introducción)
    - [Ejercicio 4 - Usando cURL](#Tema-0-Introducción)
    - [Ejercicio 5 - Práctica a Servidor Web](#Tema-0-Introducción)
- [Tema 1 - Servidores Web ](#Tema-1-Servidores-Web)
- [Tema 2 - Placeholder ](#Tema-X-Placeholder)
- [Tema 3 - Placeholder ](#Tema-X-Placeholder)

## Ejercicio 1 - Introducción :

**¿Quién, dónde y cuándo se crea el primer servidor web?**
- Tim Berners-Lee junto a Robert Cailliau fueron los creadores del primer servidor web, se creó entre 1989 y 1990 en el CERN (Conseil Européen pour la Recherche Nucléaire o Organización Europea para la Investigación Nuclear).


**¿Qué es pila de protocolos usados por http?**
- TCP/IP


**¿Componentes de una URL?**
1. Esquema/Protocolo que utiliza.
2. Nombre del dominio.
3. El puerto que utiliza (suele ser opcional, salvo casos como redes internas)
4. La ruta del archivo solicitado, tanto el nombre como su extensión de archivo.
5. La Query String dónde quedan registrados diferentes parámetros útiles para el trabajo con la base de datos. Suele ser opcional.
6. También veremos ID’s relacionadas con localizaciones dentro de un mismo archivo (por ejemplo en el caso del contenido relacionado de un índice en un manual de instrucciones.) También es un componente opcional por su naturaleza.


**¿Pasos en la recuperación de una página web mediante HTTP?**
- Se lanza una consulta desde el lado del cliente, la consulta consiste en un datagrama compuesto por un método(comando) una URI y la versión HTTP utilizada. Se recibe la consulta y el servidor la analiza y responde bien con un mensaje dónde se da a conocer el proceso funcionó junto con el archivo solicitado o bien un mensaje de error.


**Diferencia entre páginas dinámicas y estáticas**
- Las páginas dinámicas se generan en el momento a través de scripts del servidor, un ejemplo es la página de búsqueda de Google. Mientras que una estática es una página que siempre permanece igual independiente de los parámetros que se le lancen.

**¿Cómo usar telnet para acceder a un servidor web?**
- Activamos el cliente Telnet en caso de que no lo tengamos activado

**Request. Métodos principales**
- GET y POST

**Response. Códigos**
- 1XX – Informativo
- 2XX – OK
- 3XX - Redirección
- 4XX – Error
- 5XX – Errores del servidor

**Content type. Tipos principales**
- Texto / HTML

## Ejercicio 2 - UDP and TCP. Comparison of Transport Protocol :

**Diferencias entre UDP y TCP**
- TCP es más lento pero asegura que la información llegue completa y en el orden correcto, mientras que UDP es más rápido porque no asegura la transmisión completa de los datos así como del orden de llegada de estos.

**¿Qué aplicaciones usan TCP?**
- HTTP, FTP, SMTP, Telnet entre otras.


**¿Qué aplicaciones usan UDP?**
- DNS, TFTP (Trivial Files Transmission Protocol), NFS (NetWork File System), NCS (NetWork-Based Call Signaling).

**¿Qué capa almacena el puerto?**
- La capa número 4, la capa de Transporte.

**¿Qué capa almacena la IP?**

- La capa número 3, la capa de Red.

**¿Qué es Three-way Handshake?**

- Proceso en el que se establece una conexión segura entre dos dispositivos/máquinas a través de una red de conexión TCP/IP confirmando que ambas partes se encuentras listas para la comunicación.

## Ejercicio 3 - Práctica Telnet/HTTP :

**p**

## Ejercicio 4 - Usando cURL :

**p**

## Ejercicio 5 - Práctica a Servidor Web :

**p**
