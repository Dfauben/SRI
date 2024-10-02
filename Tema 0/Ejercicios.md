# Tema 0 - Introducción a HTTP 

## Indice

- [Inicio ](../README.md)
- [Tema 0 - Introducción ](#indice)
    - [Ejercicio 1 - Introducción ](#ejercicio-1---introducción-)
    - [Ejercicio 2 - Comparativa entre UDP y TCP](#ejercicio-2---udp-and-tcp-comparison-of-transport-protocol-)
    - [Ejercicio 3 - Práctica de Telnet/HTTP](#ejercicio-3---práctica-telnethttp-)
    - [Ejercicio 4 - Usando cURL](#ejercicio-4---usando-curl-)
    - [Ejercicio 5 - Práctica a Servidor Web](#ejercicio-5---práctica-a-servidor-web-)
- [Tema 1 - Servidores Web ](#Tema-1-Servidores-Web)
- [Tema 2 - Placeholder ](#Tema-X-Placeholder)
- [Tema 3 - Placeholder ](#Tema-X-Placeholder)

<br>

## Ejercicio 1 - Introducción :

<br>

### ¿Quién, dónde y cuándo se crea el primer servidor web?
- Tim Berners-Lee junto a Robert Cailliau fueron los creadores del primer servidor web, se creó entre 1989 y 1990 en el CERN (Conseil Européen pour la Recherche Nucléaire o Organización Europea para la Investigación Nuclear).

<br>

### ¿Qué es pila de protocolos usados por http?

- La pila de porotocolos TCP/IP

<br>

### ¿Componentes de una URL?

<br>

<img src="./rsc/images/URL.png" alt="urlimage" width="470"/>

<br>

1. Esquema/Protocolo que utiliza.
2. Nombre del dominio.
3. El puerto que utiliza (suele ser opcional, salvo casos como redes internas)
4. La ruta del archivo solicitado, tanto el nombre como su extensión de archivo.
5. La Query String dónde quedan registrados diferentes parámetros útiles para el trabajo con la base de datos. Suele ser opcional.
6. También veremos ID’s relacionadas con localizaciones dentro de un mismo archivo (por ejemplo en el caso del contenido relacionado de un índice en un manual de instrucciones.) También es un componente opcional por su naturaleza.

<br>

### ¿Pasos en la recuperación de una página web mediante HTTP?
- Se lanza una consulta desde el lado del cliente, la consulta consiste en un datagrama compuesto por un método(comando) una URI y la versión HTTP utilizada. Se recibe la consulta y el servidor la analiza y responde bien con un mensaje dónde se da a conocer el proceso funcionó junto con el archivo solicitado o bien un mensaje de error.

<br>

### Diferencia entre páginas dinámicas y estáticas
- Las páginas dinámicas se generan en el momento a través de scripts del servidor, un ejemplo es la página de búsqueda de Google. Mientras que una estática es una página que siempre permanece igual independiente de los parámetros que se le lancen.

<br>

### ¿Cómo usar telnet para acceder a un servidor web?
1. Activamos el cliente Telnet en caso de que no lo tengamos activado. Para ello accedemos a ***"Activar o desactivar las características de Windows"*** y buscamos la opción de **cliente de Telnet**.

<br>

<img src="./rsc/images/Telnetallw.png" alt="logos" width="340"/>

</br>

2. Con Telnet ya activado, abrimos la línea de comandos y ejecutamos el comando de **Telnet** para comunicarnos con un servidor web, lo hacemos con el siguiente comando

``telnet Nombre_Dominio Puerto
``

Podemos acompañar con la ejecución del comando, una petición a través de ***GET***, lo que nos daría información relativa a la comunicación que hemos establecido. En la siguiente imagen vemos un ejemplo.

<img src="./rsc/images/Telnet out.png" alt="logos" width="540"/>

<br>



### Request. Métodos principales

| Método | Descripción |
|:-:|:-:|
| GET | Solicita un recurso |
| HEAD | Al igual que GET solicita un recurso, pero sin el *BODY* del recurso (Solo *HEAD*) |
| POST | Envío de un recurso|
| PUT | Parecido a POST salvo que PUT es un método idempotente (la reiteración a su llamada no tiene un efecto)|
| DELETE | Borra un recurso |
| CONNECT | Crea un túnel de conexión con el servidor con el recurso como identificador |
| OPTIONS | Permite describir opciones de comunicación para el recurso de destino |
| TRACE | Realiza una prueba en la que se obtiene información del envío del recurso|
| PATCH | Aplica modificaciones parciales a un recurso|

<br>


### Response. Códigos

<br>

| Nº Código | Descripción  |
|:-:|:-:|
| 100-199 |  Respuesta informativa |
| 200-299 | Respuesta satisfactoria |
| 300-399 | Redirección |
| 400-499 | Error del cliente |
| 500-599 | Error del servidor |

<br>


### Content type. Tipos principales

<br>

<table>
    <th>Tipo</th>
    <th>Formato</th>
    <tr>
        <td rowspan="2">Aplicación</td>
        <td>PDF</td>
    </tr>
    <tr>
        <td>XML</td>
    </tr>
    <tr>
        <td rowspan="2">Audio</td>
        <td>ogg</td>
    </tr>
    <tr>
        <td>mpeg</td>
    </tr>
        <tr>
        <td rowspan="2">Imagen</td>
        <td>apng</td>
    </tr>
    <tr>
        <td>jpeg</td>
    </tr>
        <tr>
        <td rowspan="4">Texto</td>
        <td>css</td>
    </tr>
    <tr>
        <td>html</td>
    </tr>
    <tr>
        <td>php</td>
    </tr>
    <tr>
        <td>xml</td>
    </tr>
    <tr>
        <td>Video</td>
        <td>mp4</td>
    </tr>
</table>


<br>
<br>

## Ejercicio 2 - UDP and TCP. Comparison of Transport Protocol :

### Diferencias entre UDP y TCP
- TCP es más lento pero asegura que la información llegue completa y en el orden correcto, mientras que UDP es más rápido porque no asegura la transmisión completa de los datos así como del orden de llegada de estos.

<br>

### ¿Qué aplicaciones usan TCP?
- HTTP, FTP, SMTP, Telnet entre otras.

<br>

### ¿Qué aplicaciones usan UDP?
- DNS, TFTP (Trivial Files Transmission Protocol), NFS (NetWork File System), NCS (NetWork-Based Call Signaling).

<br>

### ¿Qué capa almacena el puerto?
- La capa número 4, la capa de Transporte.

<br>

### ¿Qué capa almacena la IP?

- La capa número 3, la capa de Red.

<br>

### ¿Qué es Three-way Handshake?

- Proceso en el que se establece una conexión segura entre dos dispositivos/máquinas a través de una red de conexión TCP/IP confirmando que ambas partes se encuentras listas para la comunicación.

<br>
<br>

## Ejercicio 3 - Práctica Telnet/HTTP :

### p

<br>
<br>

## Ejercicio 4 - Usando cURL :

El comando cURL abreviatura de ***Client URL*** nos permite conectarnos a una URL y demostrar así la conectividad que mantenemos con esta URL. Además este comando nos permite una serie de opciones:

- **-O** : Descarga el archivo y lo guarda con el mismo nombre que la URL.
- **-k** : Permite la conexión a webs SSL sin certificado (Peligroso).
- **-s** : Reduce la cantidad información mostrada de la conexión.
- **-u** : Permite introducir credenciales.

**Si añadimos al final del comando ">" con un nombre que queramos y una extensión correcta podemos guardar más personalizado**

``
cURL 'Nombre del dominio' > Nombre_archivo.html
``

<img src="./rsc/images/cURL.png" alt="logos" width="480"/>

<br>
<br>

## Ejercicio 5 - Práctica a Servidor Web :

Existen varias formas de crear un hosting improvisado para nuestro servidor, veamos como hacerlo junto a **Python**

### Método 1 - Simple web server

1. Con **Python** instalado es tan sencillo como ejecutar en una consola el siguiente comando

``python -m http.server 8000
`` 

<img src="./rsc/images/serverhost.png" alt="pthnsrv" width="480"/>

<br>

2. Ahora si accedemos desde nuestro navegador web a *'localhost'*, podemos observar que funciona correctamente

<br>

**Nota: En caso de que no tengamos preparado un documento html, aparecerá el sistema de archivos de la máquina, algo que puede llegar a ser bastante peligroso**.

### 
