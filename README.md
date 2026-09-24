# Servicios en red e Internet

Descripción del módulo de servicios en red e Internet

# Tema 0 Introducción

elemento | Descripción
-------- | -----------
Elemento | Descripción
Ejercicio 1 | Este es el ejercicio 1
Ejercicio 2 | Este es el ejercicio 2
Ejercicio 3 | Este es el ejercicio 3
Ejercicio 4 | Este es el ejercicio 4

# Actividad 0.1 - HTTP Introduction

# ¿Quién, dónde y cuándo se crea el primer servidor web?

El primer servidor web del mundo fue creado por el científico británico Tim Berners-Lee. CERN (Organización Europea para la Investigación Nuclear), situado en Ginebra, Suiza. Se desarrolló a finales de 1990 (la primera página web estuvo lista en diciembre de 1990) y se puso en línea y disponible para el público general el 6 de agosto de 1991.

# ¿Qué es pila de protocolos usados por http?

Es el conjunto de capas de comunicación de la arquitectura TCP/IP donde HTTP opera en la cima como el lenguaje de la aplicación.

# ¿Componentes de una URL?

Una URL (Uniform Resource Locator) es la dirección específica que se utiliza para acceder a un recurso en Internet. Sus componentes principales son:

Esquema o Protocolo: Especifica el protocolo utilizado para recuperar el recurso (por ejemplo, http, https, ftp).

Subdominio: Indica el subapartado del dominio principal (por ejemplo, www).

Dominio o Host: El nombre de dominio único asignado al servidor web (por ejemplo, ejemplo.com).

Puerto: El canal de comunicación del servidor (por ejemplo, :80 para HTTP o :443 para HTTPS). Suele estar oculto si es el predeterminado.

Ruta (Path): La ubicación específica del recurso o archivo dentro del servidor (por ejemplo, /productos/index.html).

Parámetros de consulta (Query): Datos adicionales enviados al servidor que empiezan con ? (por ejemplo, ?id=123&categoria=libros).

Anclaje o Fragmento: Apunta a una sección interna específica de la página, identificado con # (por ejemplo, #contacto).   

# ¿Pasos en la recuperación de una página web mediante HTTP?

El proceso que ocurre desde que escribes una URL en el navegador hasta que ves la página consta de los siguientes pasos secuenciales:

Resolución de DNS: El navegador traduce el nombre de dominio (ejemplo.com) en una dirección IP numérica mediante el sistema DNS.

Establecimiento de la conexión: El navegador abre una conexión TCP/IP con el servidor web (habitualmente usando el puerto 80 o 443).

Envío de la solicitud (HTTP Request): El navegador envía un mensaje HTTP al servidor solicitando el recurso.

Procesamiento del servidor: El servidor web recibe la solicitud, busca el archivo o ejecuta el código necesario para generar la respuesta.

Envío de la respuesta (HTTP Response): El servidor devuelve un mensaje HTTP que incluye un código de estado y el contenido del recurso (HTML, imágenes, etc.).

Renderizado del navegador: El navegador interpreta el código HTML, descarga recursos adicionales (CSS, JS) y dibuja la página en la pantalla.

# Diferencia entre páginas dinámicas y estáticas

Las páginas estáticas muestran siempre la misma información fija a todos los visitantes, mientras que las páginas dinámicas generan contenido en tiempo real según la interacción del usuario o una base de datos. 

# Actividad 0.2 - UDP and TCP: Comparison of Transport Protocols

# Diferencias entre udp y tcp? (min 2:46 y 4:15)

El protocolo TCP garantiza una entrega de datos segura y ordenada a costa de ser más lento, mientras que el protocolo UDP prioriza la velocidad máxima sin importar si se pierden algunos paquetes.

# ¿Qué aplicaciones usan tcp?

http, smtp, pop, imap, ssh

# ¿Qué aplicaciones usan udp?

DNS (resolución de nombres, también usa TCP para consultas grandes).
DHCP (asignación dinámica de IPs).
VoIP (llamadas de voz por internet) y videollamadas.
Streaming de video en vivo.
Juegos en línea rápidos.

# ¿Qué capa almacena el puerto?

La capa de transporte

# ¿Qué capa almacena la dirección IP?

La capa de red

# ¿Qué es three-way handshake?

Es el proceso de establecimiento de conexión de tres pasos que usa TCP antes de enviar datos reales.

SYN: El cliente envía un paquete de sincronización al servidor.
SYN-ACK: El servidor responde aceptando la sincronización.
ACK: El cliente confirma la respuesta del servidor y la conexión queda abierta para transmitir datos.

    
    
