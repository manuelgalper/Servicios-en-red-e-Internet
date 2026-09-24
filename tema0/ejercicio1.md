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

¿Cómo usar telnet para acceder a un servidor web?

Telnet permite simular manualmente el comportamiento de un navegador web enviando peticiones HTTP directas a través de la terminal de comandos.

       Abrir la conexión: Abre la terminal y conéctate al dominio por el puerto 80 escribiendo:
bash
telnet ejemplo.com 80
Usa el código con precaución.
       Escribir la petición HTTP: Una vez conectado (la pantalla se quedará en blanco esperando tu entrada), debes escribir el método de petición y el host obligatoriamente:
http
GET / HTTP/1.1
Host: ejemplo.com
Usa el código con precaución.
       
       Enviar la solicitud: Pulsa la tecla Intro dos veces (una línea en blanco indica el fin de las cabeceras). El servidor responderá con el código HTTP y el código HTML de la página.

# (solución en actividad 0.3) Request. Métodos principales

Los métodos HTTP indican la acción concreta que se desea realizar sobre el recurso del servidor:

GET: Solicita la representación de un recurso específico. Solo debe recuperar datos y no modificar el estado del servidor.

POST: Envía datos al servidor para que se procesen o para crear un nuevo recurso (por ejemplo, al enviar un formulario de registro).

PUT: Reemplaza por completo el recurso de destino con los datos enviados en la petición.

PATCH: Aplica modificaciones parciales a un recurso ya existente.

DELETE: Borra el recurso especificado en el servidor.

# Response. Códigos

Los códigos de estado HTTP constan de tres dígitos y notifican si la petición se completó correctamente o si hubo un error. Se agrupan en cinco categorías:

1xx (Informativos): La petición fue recibida y el proceso continúa (ej. 100 Continue).

2xx (Éxito): La acción se recibió, entendió y aceptó correctamente (ej. 200 OK, 201 Created).

3xx (Redirecciones): Se requiere realizar acciones adicionales para completar la solicitud (ej. 301 Moved Permanently, 302 Found).

4xx (Errores del Cliente): La solicitud contiene sintaxis incorrecta o no puede procesarse (ej. 400 Bad Request, 401 Unauthorized, 404 Not Found).

5xx (Errores del Servidor): El servidor falló al intentar procesar una solicitud que parecía válida (ej. 500 Internal Server Error, 503 Service Unavailable).


  
