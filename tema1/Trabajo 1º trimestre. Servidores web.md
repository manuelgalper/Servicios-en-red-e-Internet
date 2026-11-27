Vamos a instalar un servidor web interno para un instituto. Se Pide:

# Instalación del servidor web apache. Usaremos dos dominios mediante el archivo hosts: centro.intranet y departamentos.centro.intranet. 
# El primero servirá el contenido mediante wordpress y el segundo una aplicación en python

Para simular los dominios internos en el servidor (y en los equipos clientes de prueba), editamos el archivo /etc/hosts y luego apuntamos 
los nombres a la IP del servidor (o 127.0.0.1 en local).

sudo nano /etc/hosts

<img width="459" height="24" alt="image" src="https://github.com/user-attachments/assets/1d0abeaf-7210-453c-b759-e8901024ca5f" />

Añadimos la siguiente línea:
text
127.0.0.1   centro.intranet departamentos.centro.intranet servidor2.centro.intranet

<img width="806" height="264" alt="image" src="https://github.com/user-attachments/assets/af0f03ec-83f6-491a-86bd-50a8fc9da6a4" />

Ahora para comprobar que funciona hacemos ping para comprobar si apuntan correctamente a nuestro equipo local

ping -c 2 centro.intranet

Y vemos que se muestra que el dominio centro.intranet resuelve directamente a 127.0.0.1 con un 0% de pérdida de paquetes 
(2 packets transmitted, 2 received).

<img width="512" height="148" alt="image" src="https://github.com/user-attachments/assets/04028d8a-9f07-4c0f-be35-646f41431a41" />

Ahora hacemos lo mismo con los otros dos subdominios que hemos creado

ping -c 1 departamentos.centro.intranet && ping -c 1 servidor2.centro.intranet

Y vemos que los tres dominios resuelven correctamente a 127.0.0.1. Como vemos tanto departamentos.centro.intranet como servidor2.centro.intranet 
responden sin pérdida de paquetes (aparece centro.intranet en la salida porque ping muestra el primer nombre asociado a esa IP en /etc/hosts)

<img width="841" height="221" alt="image" src="https://github.com/user-attachments/assets/a5a24388-6015-4313-84d5-eb84bc570723" />

# Activar los módulos necesarios para ejecutar php y acceder a mysql

Instala el servidor web Apache, el gestor de bases de datos MariaDB/MySQL, PHP con sus extensiones necesarias y el módulo libapache2-mod-wsgi-py3 para ejecutar Python.

# Instalación de Apache

# Paso 1: Instalar Apache y actualizar el firewall

Una vez iniciado la máquina de Ubuntu empiezo con la instalación de Apache, para ello escribo en el terminal los siguientes comandos:

sudo apt update

sudo apt install apache2

<img width="541" height="156" alt="image" src="https://github.com/user-attachments/assets/ad888f26-3825-4c82-ac29-fc8b1907f09b" />

Ahora nos pide confirmar la instalación tecleo la letra S y el proceso continuará ejecutándose

<img width="532" height="243" alt="image" src="https://github.com/user-attachments/assets/70878e14-129c-46c5-bbe3-f74b81416301" />

<img width="537" height="313" alt="image" src="https://github.com/user-attachments/assets/124d1b61-bffd-4822-a32a-f70f208bae33" />

<img width="538" height="364" alt="image" src="https://github.com/user-attachments/assets/f2f51b62-8a08-4a3a-aaae-837bb69a1981" />

Ahora me voy al navegador y escribo http://localhost y vemos que ya sale la página web predeterminada de Apache para Ubuntu:

<img width="668" height="568" alt="image" src="https://github.com/user-attachments/assets/2cd2c641-8940-459c-8b30-ded367101516" />

# Paso 2: Instalar MySQL

Lo siguiente que vamos a hacer es instalar un sistema de base de datos para poder almacenar y gestionar los datos que es el Mysql,
para ello, escribo el siguiente comando

sudo apt install mysql-server

<img width="515" height="31" alt="image" src="https://github.com/user-attachments/assets/e8c459d4-b031-4d92-971a-0d3ca68ebf45" />

Ahora nos pide confirmar la instalación tecleo la letra S y el proceso continuará ejecutándose

<img width="476" height="367" alt="image" src="https://github.com/user-attachments/assets/281f857b-d0ad-4a2a-98b5-a101ec9faf77" />

Y una vez que haya confirmado la instalación el proceso continua ejecutándose

<img width="543" height="358" alt="image" src="https://github.com/user-attachments/assets/7475419d-f4dd-4676-82c1-6083904d8651" />

<img width="542" height="373" alt="image" src="https://github.com/user-attachments/assets/ecfb7644-6753-4128-84c1-257954959e77" />

<img width="507" height="317" alt="image" src="https://github.com/user-attachments/assets/6d2f3524-83be-41fc-bc56-ad46837fef46" />

<img width="543" height="364" alt="image" src="https://github.com/user-attachments/assets/50e5a048-6577-4b4b-9647-09e39f492631" />

Una vez que se haya completado la instalación se recomienda ejecutar una secuencia de comandos de seguridad que viene preinstalada en MySQL,
para ello ejecuto lo siguiente:

sudo mysql_secure_installation

<img width="518" height="31" alt="image" src="https://github.com/user-attachments/assets/6c0ce924-aa81-45da-9170-cfa70e5f7afb" />

Ahora nos pide solicitar la instalación le digo Y y luego ENTER

<img width="518" height="259" alt="image" src="https://github.com/user-attachments/assets/2cfa8d6b-016a-4d80-b723-fffcaddac895" />

<img width="538" height="360" alt="image" src="https://github.com/user-attachments/assets/1a069dfc-05f5-4fdb-9fcd-676ac49a98e9" />

Cuando se haya terminado compruebo si se puede iniciar sesión en la consola de MySQL, para ello escribo el siguiente comando:

sudo mysql 

Y vemos que sale el siguiente resultado:

<img width="528" height="215" alt="image" src="https://github.com/user-attachments/assets/21ea675b-67c6-4583-83ed-f197df943ed8" />

Y ahora si quiero salir de la consola escribo lo siguiente:

exit

# Paso 3 Instalar PHP

Lo siguiente que vamos a hacer es instalar el servidor PHP para almacenar y gestionar sus datos, para ello escribo el siguiente comando:

sudo apt install php libapache2-mod-php php-mysql

<img width="536" height="32" alt="image" src="https://github.com/user-attachments/assets/0188f31d-b216-4906-8381-bcd5b5bec1d3" />

Ahora nos pide solicitar la instalación le digo S y luego ENTER 

Y vemos que el proceso sigue ejecutando

<img width="542" height="315" alt="image" src="https://github.com/user-attachments/assets/11b1bc6a-749f-4364-a758-8a4f3ad545d4" />

Ahora una vez que se haya completado la instalación vamos a confirmar cuál es la versión de PHP, para ello escribo lo siguiente:

php -v

<img width="360" height="16" alt="image" src="https://github.com/user-attachments/assets/d1c8c8af-7de1-4689-b40d-793fbb543edb" />

Y vemos que la versión es 8.14.11

<img width="463" height="88" alt="image" src="https://github.com/user-attachments/assets/e4b15e7c-17da-46f2-b7b5-a65bf3fc019f" />

<img width="92" height="26" alt="image" src="https://github.com/user-attachments/assets/2bc942ed-4ee2-478c-bc97-598455c3dddd" />

# Paso 4 Instalar el módulo libapache2-mod-wsgi-py3 para ejecutar Python

Para instalar el modulo libapache2-mod-wsgi-py3 para ejecutar Python lo hago con los siguientes comando

sudo apt update

sudo apt install libapache2-mod-wsgi-py3

<img width="528" height="90" alt="image" src="https://github.com/user-attachments/assets/8aa13c53-2d13-4497-b4fa-24904a5f7807" />

<img width="711" height="283" alt="image" src="https://github.com/user-attachments/assets/f527b038-e1a7-40ba-9f8b-c8cba5c657a6" />

Una vez que lo tenemos instalado habilitamos los módulos requeridos en apache

sudo a2enmod rewrite
sudo a2enmod wsgi
sudo systemctl restart apache2

<img width="517" height="93" alt="image" src="https://github.com/user-attachments/assets/559f573b-f8b0-43a3-8a2b-82c46d63ce5d" />

# Instala y configura wordpress

Para instalar y configurar wordpress lo primero que hago es acceder a mysql

sudo mysql

<img width="530" height="214" alt="image" src="https://github.com/user-attachments/assets/fd0f6a25-937a-4186-8ea1-569e305d01e2" />

Ahora creo la base de datos y su usuario

<img width="499" height="211" alt="image" src="https://github.com/user-attachments/assets/342797f5-39ce-46d5-b920-4825b1dd4d4d" />

Ahora descargamos wordpress en nuestra carpeta web

cd /tmp
wget https://wordpress.org/latest.tar.gz

<img width="833" height="199" alt="image" src="https://github.com/user-attachments/assets/023f37e6-6572-48f4-85e6-cfe6575a8ed4" />

Después descomprimo el archivo en /tmp

tar xzvf latest.tar.gz

<img width="861" height="360" alt="image" src="https://github.com/user-attachments/assets/4b275052-76ad-40b4-a7a9-b33471c24a40" />

Ahora creamos la carpeta del sitio web y copiamos los archivos

sudo mkdir -p /var/www/centro.intranet

sudo cp -a /tmp/wordpress/. /var/www/centro.intranet/

<img width="704" height="61" alt="image" src="https://github.com/user-attachments/assets/e4b89271-2e1c-4efc-8f53-37438099e481" />

Ahora le damos los permisos

sudo chown -R www-data:www-data /var/www/centro.intranet

sudo chmod -R 755 /var/www/centro.intranet

<img width="712" height="34" alt="image" src="https://github.com/user-attachments/assets/f8431590-7fb7-4ba0-beb5-83565f19d1e6" />

Ahora creamos el VirtualHost para centro.intranet, para ello abro el archivo de configuración

sudo nano /etc/apache2/sites-available/centro.intranet.conf

<img width="732" height="19" alt="image" src="https://github.com/user-attachments/assets/57e5da9a-463f-4201-aa4a-abdf2cb8080b" />

Dentro del archivo de configuración pegamos el siguiente bloque

<img width="418" height="242" alt="image" src="https://github.com/user-attachments/assets/627b9536-bbcd-49be-b472-8c3660ffccc1" />

Activamos el sitio y reiniciamos apache

sudo a2ensite centro.intranet.conf

sudo systemctl reload apache2

<img width="593" height="64" alt="image" src="https://github.com/user-attachments/assets/3afab1b5-09f5-4b7b-b694-811ee1c7d8c5" />

Ahora nos vamos al navegador y ponemos http://centro.intranet y vemos que Apache y PHP ya están sirviendo WordPress correctamente 
en http://centro.intranet

<img width="1014" height="608" alt="image" src="https://github.com/user-attachments/assets/a8e57cad-f12b-47f9-be5f-35659d0ee822" />

Para completar la instalación hago lo siguiente

Seleccionar idioma:Hago clic en Español y pulsa el botón Continuar

<img width="1014" height="604" alt="image" src="https://github.com/user-attachments/assets/972eed4d-6b64-42a2-b928-41f421e8be01" />

Conectar la base de datos: en la siguiente pantalla pulso ¡Vamos a ello! y escribo los datos que creaste en MySQL (wordpress, wpuser 
y la contraseña que le asigné)

<img width="1013" height="608" alt="image" src="https://github.com/user-attachments/assets/bdac226a-ad2b-463d-a7c9-b01f0017421f" />

<img width="1012" height="604" alt="image" src="https://github.com/user-attachments/assets/9c385f4e-a823-482d-bac0-84ab20a10362" />

Pulsamos Enviar, luego Ejecutar la instalación, rellena el título del sitio junto con mi usuario y mi contraseña de administrador 
y hago clic en Instalar WordPress.

<img width="1013" height="603" alt="image" src="https://github.com/user-attachments/assets/a3639d60-f0c1-4fce-9ea7-348f190a0f16" />

<img width="1015" height="608" alt="image" src="https://github.com/user-attachments/assets/889bf69a-af85-4fef-923e-c48802ed4a44" />

Y de esta manera ya tendríamos WordPress instalado

<img width="1014" height="606" alt="image" src="https://github.com/user-attachments/assets/be23f048-dbbe-4dc7-85ee-32bb9ab03c14" />

# Activar el módulo “wsgi” para permitir la ejecución de aplicaciones Python

Vamos a crear la aplicación wsgi, para ello creamos el directorio y el archivo de aplicación en /var/www/departamentos/app.py

sudo mkdir -p /var/www/departamentos

sudo nano /var/www/departamentos/app.py

<img width="594" height="48" alt="image" src="https://github.com/user-attachments/assets/2ebfdbee-13bf-498a-8d7f-d1c1cd2f7206" />

Ahora añado el siguiente código de prueba

<img width="859" height="493" alt="image" src="https://github.com/user-attachments/assets/49ce9392-f23e-453a-9b7a-380a23373b1f" />

Ahora le asigno los permisos

sudo chown -R www-data:www-data /var/www/departamentos

<img width="700" height="18" alt="image" src="https://github.com/user-attachments/assets/a74881e0-b8b6-4f07-a662-a5cfc258a93a" />

Ahora creamos un archivo de contraseñas para proteger el acceso (por ejemplo, para el usuario profesor), después nos pedirá la contraseña 
para el nuevo usuario y luego volver a escribir la contraseña

sudo /usr/bin/htpasswd -c /etc/apache2/.htpasswd_departamentos profesor

Y vemos que el usuario profesor y el archivo .htpasswd_departamentos se han creado correctamente

<img width="814" height="87" alt="image" src="https://github.com/user-attachments/assets/f9dcf77e-1c5d-46ad-a758-8654abefb5ce" />

Ahora creamos el archivo VirtualHost para departamentos.centro.intranet

sudo nano /etc/apache2/sites-available/departamentos.conf

<img width="829" height="21" alt="image" src="https://github.com/user-attachments/assets/4385802a-03dc-46e4-a9b3-f55bb2f44205" />

Ahora pego la siguiente configuración

<img width="858" height="489" alt="image" src="https://github.com/user-attachments/assets/59443f74-45f4-4528-9079-3c997d5e06af" />

Lo guardamos y ahora activamos el sitio y reiniciamos Apache

sudo a2ensite departamentos.centro.intranet.conf

sudo systemctl restart apache2

<img width="670" height="117" alt="image" src="https://github.com/user-attachments/assets/cf8785ae-55c1-4bcb-b6e7-06daac15d197" />

# Instala y configura awstat

Vamos instalar awstat y configurar y activar CGI en Apache lo hacemos con los siguientes comandos

sudo apt install awstats -y

sudo a2enmod cgi

<img width="677" height="516" alt="image" src="https://github.com/user-attachments/assets/cb013122-df9c-4f65-b57f-11f8e630d87d" />

Una vez instalado y configurado awstat vamos a crear una configuración específica para el dominio principal copiando la plantilla
base

<img width="842" height="31" alt="image" src="https://github.com/user-attachments/assets/26ca084c-50e1-4069-95a9-7531aff7d148" />

Ahora modificamos estas tres líneas dentro del archivo

LogFile="/var/log/apache2/centro_access.log"

SiteDomain="centro.intranet"

HostAliases="localhost 127.0.0.1 centro.intranet"

<img width="860" height="491" alt="image" src="https://github.com/user-attachments/assets/31fcd6ac-97c3-4952-91b1-5f5c39ab83f9" />

<img width="865" height="513" alt="image" src="https://github.com/user-attachments/assets/855ffb51-f0eb-487e-93c5-3e474a028b31" />

<img width="858" height="488" alt="image" src="https://github.com/user-attachments/assets/02c0d4b1-7de1-4ddd-a038-2c77f3152b26" />

Una vez modificada las tres líneas configuramos los alias en Apache para ver las estadísticas

sudo nano /etc/apache2/conf-available/awstats.conf

<img width="671" height="19" alt="image" src="https://github.com/user-attachments/assets/b0a17e6a-2e7e-48cd-b470-7d37fcadcf95" />

Ahora pegamos el siguiente contenido

<img width="863" height="488" alt="image" src="https://github.com/user-attachments/assets/b589d62e-8991-41f1-827f-54afcf1e12b3" />

Después habilitamos el módulo CGI en Apache para visualizar los informes y actualiza las estadísticas

sudo a2enconf awstats

sudo systemctl restart apache2

sudo /usr/lib/cgi-bin/awstats.pl -config=centro.intranet -update

<img width="769" height="469" alt="image" src="https://github.com/user-attachments/assets/6db8bce7-1703-461f-bfbb-ebca2dc5ee74" />

# Instala un segundo servidor de tu elección (nginx, lighttpd) bajo el dominio “servidor2.centro.intranet”. Debes configurarlo para 
# que sirva en el puerto 8080 y haz los cambios necesarios para ejecutar php. Instala phpmyadmin.

En este último apartado vamos a haber cómo instalar un segundo servidor web (Nginx en puerto 8080) + PHP + phpMyAdmin 
(servidor2.centro.intranet, para ello lo hago con el siguiente comando

Para instalar Nginx, PHP-FPM, lo hacemos con el siguiente comando 

sudo apt install nginx php-fpm phpmyadmin -y

<img width="642" height="22" alt="image" src="https://github.com/user-attachments/assets/821f5634-3b66-4e95-9ea3-1e95a59a12c2" />

<img width="640" height="133" alt="image" src="https://github.com/user-attachments/assets/99448f8f-458e-416e-967a-5764a15c53ad" />







