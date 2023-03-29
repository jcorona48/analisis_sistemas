
# Presentación

* Materia: Analisis de Sistemas
* Maestro: Lizandro
* Nombre: Joan Elias
* Apellido: Corona Gómez
* Matricula: 2021-0981
* Periodo: P1-2023


# Introduccion
En este documento se presentará la documentación detallada de un programa de una aplicación web, que ha sido diseñado para almacenar información de usuarios en una base de datos Postgres y Redis, realizar cálculos complejos en un worker y presentar los resultados en una página web mediante el uso de un cliente React. La aplicación ha sido empaquetada en Docker con seis servicios: nginx, postgres, api, redis, client-react y worker. La documentación incluirá una introducción a la aplicación y su funcionamiento, un marco teórico que explicará los componentes y tecnologías utilizadas, una prueba de funcionamiento detallada y una conclusión que destacará los resultados y posibles mejoras para el futuro. Este proyecto es una excelente oportunidad para comprender las distintas partes que conforman una página web profesional, y cómo se integran para brindar una experiencia de usuario satisfactoria.

# Marco teorico

Como mencioné en un inicio utilizamos varias herramientas y tecnologias, entre estas están:

## Postgres
Que es un manejador de base de datos SQL, que nos permitirá almacenar la información que digitamos en nuestro programa.

## Nginx

Este servicio nos permite controlar todas las direcciones y puertos a travez de un mismo puerto. Logrando interconectar el cliente con el Api sin necesidad de abarcar otro puerto del equipo.

## Node Js - Api Rest

Este servicio nos permite la conexión entre nuestros servicios de redis y Postgres al cliente, que en este caso utilizamos el framework de React. Utilizando librerias como Express, que nos permite el control de las solicitudes get, post, path, etc..., así como la libreria axios para hacer las solicitudes a nuestras bases de datos.

## Redis

Este servicio nos permite almacenar la información en la caché para un rapido acceso a esta. Para almacenar los datos utiliza el formato Clave y Valor.

## React

Este framework nos permite trabajar mas dinamicamente con JavaScript, el cual permite interpretar directamente el codigo HTML junto a JavaScript. Este es uno de los Framework mas populares en la actualidad de FrontEnd.

## Docker

Esta herramienta introduce un nuevo termino que son los contenedores, con estos almacenamos cada uno de los servicios por separado (Como si estuvieran en servidores totalmente distintos). Los contenedores corren con base de linux asi que son compatibles con alta cantidad de equipos.


# Prueba de funcionamiento.
Click en la Imagen.

[![Video De Prueba de funcionamiento](https://www.atestrategiasysoluciones.com/wp-content/uploads/2020/08/El-v%C3%ADdeo-es-el-rey.jpg)](https://drive.google.com/file/d/1UZdMNFNL4fXeBUoEGWZQ3V0nspR2LUnM/view?usp=sharing "Prueba de Funcionamiento.")


# Conclusión

El analisis de estre proyecto nos ayuda a comprender como interactuan las diferentes partes en un sistema con multiples servicios. Tambien nos ubican en las nuevas tecnologías que se están utilizando hoy en dia. 

En este proyecto se pueden ubicar los archivos mas importantes, entre estos estan:

### client/src/Fib.js
Este archivo es el que se encarga de manejar el input, el envio de la información, la actualización de la informacion y el muestreo en pantalla.

### nginx/default.conf

Este archivo configura al nginx para conectar el api y el cliente en uno solo, permitiendo acceder a ellos mediante un unico puerto.

### Server/index.js
Este archivo es el que se encarga de recibir todas las consultas get y post, asi como enviar esa informacion a la base de datos. Tambien contiene un codigo especifico de redis que publica el canal insert, el cual permite el el worker pueda funcionar.

### Worker/index.js
Este archivo espera suscrito al canal insert y cuando envian la publicacion este obtiene el indice y realiza el calculo, para su posterior almacenamiento en redis.

### docker-compose.yml
Gracias a este archivo se crean todos los contenedores necesarios bajo un nombre en especifico y se conectan internamente entre ellos mediante la red interna que crea.

### */keys.js
Estos archivos almacenan las credenciales necesarias para la conexion a las diferentes bases de datos.

### client/public/index.html

Este es el archivo donde se carga toda la informacion enviada por react, gracias al div que tiene el ID " root ", sin este no se mostraria nada de la aplicacion.

## Posibles mejoras
Tras analizar profundamente el codigo del proyecto, he localizado varios casos de mejora:

* Comenzando con la actualización automática de la pantalla cuando envio la información a travéz del submit.
* El diseño poco encantador 
* La forma en la que se enseña la información.
* Avisos al digitar algun numero mayor a 40
* Control de errores cuando el usuario no digita un número.