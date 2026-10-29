# Actividad #1

Busca información sobre las siguientes directivas y el valor que toman por defecto y el lugar donde se encuentra definida.

# Directivas de identificación

# ServerName

Valor que toma por defecto: Nombre del servidor y puerto

Lugar donde se encuentra definida: #sites-enable/000-default www.example.com

# ServerAdmin

Valor que toma por defecto: Email administrador apache

Lugar donde se encuentra definida: #sites-enable/000-default webmaster@localhost

# ServerTokens

Valor que toma por defecto: Información a incluir en las cabeceras de respuesta

Lugar donde se encuentra definida: #apache2.conf Full

# Directivas de localización de ficheros

# DocumentRoot

Valor que toma por defecto: Establece el directorio donde se servirán los documentos

Lugar donde se encuentra definida: #sites-enable/000-default /var/www/html

# ErrorLog	

Valor que toma por defecto: Archivo log (bitácora) donde se almacenan los errores

Lugar donde se encuentra definida: #sites-enable/000-default ${APACHE_LOG_DIR}/error.log

APACHE_LOG_DIR está definida en /etc/apache2/envvars..
		export APACHE_LOG_DIR=/var/log/apache2

# CustomLog	

Valor que toma por defecto: Archivo de bitácora (log)

Lugar donde se encuentra definida: #sites-enable/000-default ${APACHE_LOG_DIR}/access.log

# ServerRoot

Valor que toma por defecto: Directorio donde está alojado el servidor

Lugar donde se encuentra definida: #apache2.conf /etc/apache2

# Directivas de control de la conexión

# Timeout

Valor que toma por defecto: Cantidad de tiempo que el servidor esperará para que ocurra determinados eventos antes de cerrar una petición

Lugar donde se encuentra definida: #apache2.conf Timeout 60

# KeepAlive 

Valor que toma por defecto: Permite que se puedan enviar múltiples peticiones sobre la misma conexión TCP

Lugar donde se encuentra definida: #apache2.conf KeepAlive on

# MaxKeepAliveRequests

Valor que toma por defecto: Limita el número de peticiones permitidas por conexión

Lugar donde se encuentra definida: #apache2.conf MaxKeepAliveRequests 100

# KeepAliveTimeout

Valor que toma por defecto: Tiempo que el servidor esperará peticiones subsiguientes en conexiones persistentes

Lugar donde se encuentra definida: #apache2.conf KeepAliveTimeout 5

# Otras

# LogLevel

Valor que toma por defecto: Indica el nivel de verborrea de Apache

Lugar donde se encuentra definida: #apache2.conf LogLevel warn

# LogFormat 

Valor que toma por defecto: formato del fichero de bitácora

Lugar donde se encuentra definida: #apache2.conf
# The following directives define some format nicknames for use with
# a CustomLog directive.
LogFormat "%v:%p %h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" vhost_combined
LogFormat "%h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %O" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent
		
		#000-default.conf
CustomLog ${APACHE_LOG_DIR}/access.log combined


