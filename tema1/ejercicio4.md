# Actividad #2

Busca información sobre las siguientes directivas. Indica para que se usan y escribe un ejemplo que hayas encontrado.

# <IfModule>

Es una sección en la que escribimos directivas condicionadas por la presencia de un módulo
https://httpd.apache.org/docs/2.4/mod/core.html#ifmodule
# /etc/apache2/ports.conf
<IfModule ssl_module>
    Listen 443
</IfModule>

# LoadModule

Carga un módulo Apache
	https://httpd.apache.org/docs/2.4/mod/mod_so.html#loadmodule
	# /etc/apache2/mods-enabled/alias.load
	LoadModule alias_module /usr/lib/apache2/modules/mod_alias.so

# Include

Permite la inclusión de archivos de configuración
https://httpd.apache.org/docs/2.4/mod/core.html#include
	# /etc/apache2/apache2.conf
	Include ports.conf

# <Directory>

Se utilizan para incluir directivas que afectarán a un directorio y los subdirectorios incluidos en él
https://httpd.apache.org/docs/2.4/mod/core.html#directory
	# /etc/apache2/apache2.conf
<Directory />
    Options FollowSymLinks
    AllowOverride None
    Require all denied
</Directory>

# <Files>

Se usan para incluir directivas que afectará a un fichero o grupo de ficheros (usando caracteres comodín)
https://httpd.apache.org/docs/2.4/mod/core.html#files
	# /etc/apache2/apache2.conf
	<FilesMatch "^\.ht">
    Require all denied
</FilesMatch>

# <Location>

Se utilizan para incluir directivas que afectarán a una URL
	https://httpd.apache.org/docs/2.4/mod/core.html#location
	# /etc/apache2/mods-enabled/status.conf
	<Location /server-status>
   		SetHandler server-status
   	 	Require local
   	#Require ip 192.0.2.0/24
</Location>

# <VirtualHost>

Se utilizan para incluir directivas que afectarán a un servidor virtual
	https://httpd.apache.org/docs/2.4/mod/core.html#virtualhost
# /etc/apache2/sites-enabled/000-default.conf
<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/html
</VirtualHost *:80>

# ¿Qué son los ficheros .htaccess?

Proporcionan un mecanismo para hacer cambios en la configuración por directorios.
https://httpd.apache.org/docs/2.4/howto/htaccess.html

