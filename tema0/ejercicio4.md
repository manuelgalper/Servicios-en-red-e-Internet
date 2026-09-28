# Actividad 0.4 - Usando cUrl

# Busca información sobre el comando curl y muestra al menos cinco ejemplos de uso

El comando curl (Client URL) es una herramienta de línea de comandos utilizada para transferir datos desde o hacia un servidor utilizando una gran variedad de protocolos (como HTTP, HTTPS, FTP, SFTP, entre otros). Es ampliamente utilizado por desarrolladores y administradores de sistemas para probar API, descargar archivos y automatizar interacciones en la web.

A continuación, se presentan cinco ejemplos prácticos de uso basados en su documentación oficial:

# Realizar una petición básica (Obtener el contenido de una web)
Es el uso más simple. Muestra el código fuente HTML o la respuesta de la URL especificada directamente en la terminal.
bash
curl https://example.com

# Descargar un archivo guardándolo con su nombre original
Al usar la opción -O (O mayúscula), curl descarga el archivo y lo guarda en tu equipo manteniendo el mismo nombre que tiene en el servidor.
bash
curl -O https://curl.se/docs/manual.html

# Descargar un archivo y asignarle un nombre diferente
Si prefieres guardar el archivo descargado con un nombre específico en tu disco local, debes utilizar la opción -o (o minúscula) seguida del nombre deseado.
bash
curl -o mi_manual.html https://curl.se/docs/manual.html

# Ver las cabeceras HTTP de una respuesta
Si solo necesitas inspeccionar los metadatos del servidor (como el tipo de servidor, el estado de la respuesta HTTP, cookies o la fecha) sin descargar todo el contenido, utiliza la opción -I (i mayúscula).
bash
curl -I https://curl.se

# Enviar datos en una petición POST (Simulación de formulario o API)
Para enviar información a un servidor (por ejemplo, al probar una API REST o enviar un formulario), se utiliza la opción -d seguida de los datos que se quieren transmitir.
bash
curl -d "nombre=Juan&usuario=juan123" https://example.com
