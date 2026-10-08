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

<img width="92" height="26" alt="image" src="https://github.com/user-attachments/assets/2bc942ed-4ee2-478c-bc97-598455c3dddd" />

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

# Paso 4: Crear un host virtual para su sitio web

Ahora vamos a crear un host virtual para su sitio web, lo primero que hago es crear un directorio para your_domain y lo hago con 
el siguiente comando:

sudo mkdir /var/www/your_domain

<img width="521" height="49" alt="image" src="https://github.com/user-attachments/assets/d74395c3-8bdf-4eb7-929e-998a6bcd17e1" />

A continuación, le asigno la propiedad del directorio con la variable de entorno $USER, que que es la que hará referencia a su 
usuario de sistema actual, para ello escribo lo siguiente:

sudo chown -R $USER:$USER /var/www/your_domain

<img width="585" height="52" alt="image" src="https://github.com/user-attachments/assets/729b52ec-df9f-430a-a0c3-7ed32a2afa57" />

Luego abro un nuevo un nuevo archivo de configuración en el directorio sites-available de Apache usando el editor de línea de 
comandos, en mi caso utilizo nano

sudo nano /etc/apache2/sites-available/your_domain.conf

<img width="579" height="34" alt="image" src="https://github.com/user-attachments/assets/857cc5b2-63eb-47d4-b27e-292570f04629" />

De esta manera, se creará un nuevo archivo en blanco, ahora lo que es copiar y pego la siguiente configuración básica:

<img width="586" height="365" alt="image" src="https://github.com/user-attachments/assets/a6d9fd95-8dab-48e4-b90a-50ceb21d4d06" />

Con esta configuración de VirtualHost, le indicamos a Apache que proporcione your_domain usando /var/www/your_domain como directorio 
root web

Ahora para habilitar el nuevo host virtual escribo el siguiente comando

sudo a2ensite your_domain

<img width="497" height="82" alt="image" src="https://github.com/user-attachments/assets/a84b5ee6-a504-449e-b33e-8db63d73b2b9" />

Ahora una vez habilitado el nuevo host virtual sería conveniente deshabilitarlo el sitio web predeterminado que viene instalado 
con Apache. Para deshabilitar el sitio web predeterminado de Apache, escribo lo siguiente:

sudo a2dissite 000-default

<img width="513" height="84" alt="image" src="https://github.com/user-attachments/assets/6a0758ea-ba00-4de8-a297-edfd823333d7" />

Para asegurar de que el archivo de configuración no contenga errores de sintaxis, ejecuto lo siguiente:

sudo apache2ctl configtest

<img width="694" height="79" alt="image" src="https://github.com/user-attachments/assets/ce730337-daf0-49bf-ae5a-ec7ba8e2abaf" />

Por último, vuelvo a cargar Apache para que estos cambios surtan efecto, lo hago con el siguiente comando

sudo systemctl reload apache2

<img width="510" height="28" alt="image" src="https://github.com/user-attachments/assets/94945dd2-4568-4a71-ba87-7f22307309c8" />

Ahora, vemos que el nuevo sitio web está activo, pero el directorio root web /var/www/your_domain todavía está vacío. Entonces lo
que hago es crear un archivo index.html en esa ubicación para poder probar que el host virtual funcione según lo previsto:

nano /var/www/your_domain/index.html

<img width="558" height="15" alt="image" src="https://github.com/user-attachments/assets/68c218cb-c2ab-4d3b-9a37-c7622464a672" />

Y ahora incluyo el siguiente contenido en este archivo:

<img width="436" height="37" alt="image" src="https://github.com/user-attachments/assets/4aedd4b6-ee5c-4ad8-a65c-d308b7a1e262" />

Ahora, me voy al navegador, escribo http://localhost y vemos que sale una página como la siguiente

<img width="1012" height="641" alt="image" src="https://github.com/user-attachments/assets/2eaf44df-1f15-42a8-842a-90eeb471bec5" />

Y vemos que el host virtual de Apache está funcionando según lo previsto

# Nota sobre DirectoryIndex en Apache

Para cambiar este comportamiento se deberá editar el archivo /etc/apache2/mods-enabled/dir.conf y modificar el orden en el que el 
archivo index.php se enumera en la directiva DirectoryIndex, para ello escribo el siguiente comando

sudo nano /etc/apache2/mods-enabled/dir.conf

<img width="621" height="24" alt="image" src="https://github.com/user-attachments/assets/fb25a92b-7b6f-45b2-98d9-a5ee4e9e19fd" />

<img width="570" height="55" alt="image" src="https://github.com/user-attachments/assets/eea6cbe3-c389-4d96-90c5-92dc0abd872e" />

Después de guardar y cerrar el archivo, me deberá volver a cargar Apache para que los cambios surtan efecto

sudo systemctl reload apache2

<img width="515" height="35" alt="image" src="https://github.com/user-attachments/assets/f05a1fd8-0474-4bfa-99ea-d7b76a4bddd8" />

En el siguiente paso, creamos una secuencia de comandos PHP para probar que PHP esté correctamente instalado y configurado 
en nuestro servidor.

# Paso 5: Probar el procesamiento de PHP en su servidor web

En este apartado que dispone de una ubicación personalizada para alojar los archivos y las carpetas de su sitio web, vamos a 
crear una secuencia de comandos PHP de prueba para verificar que Apache pueda gestionar solicitudes y procesar solicitudes de 
archivos PHP. Lo primero que hago es crear un archivo nuevo llamado info.php dentro de la carpeta root web personalizada

nano /var/www/your_domain/info.php

<img width="545" height="22" alt="image" src="https://github.com/user-attachments/assets/a073bfa5-25af-4c1a-84ab-270ddff6cb14" />

Con este comando se abrirá un archivo vacío. Ahora añado el siguiente texto, que es el código PHP válido, dentro del archivo

<img width="691" height="122" alt="image" src="https://github.com/user-attachments/assets/63d769ff-9c67-4173-94fd-904556ab39cf" />

Cuando haya terminado, guardo y cierro el archivo

Para probar esta secuencia de comandos, me voy al navegador, escribo http://localhost/info.php y sale la siguiente página

<img width="1016" height="576" alt="image" src="https://github.com/user-attachments/assets/b710b8a6-367d-437e-801e-62bc63f237bf" />

En esta página, se proporciona información básica sobre su servidor desde la perspectiva de PHP. Es útil para la depuración y para 
asegurarse de que sus ajustes se apliquen correctamente

Si puede ver esta página en su navegador, su instalación de PHP funciona según lo previsto

# Paso 6: Probar la conexión con la base de datos desde PHP (opcional)

En este último apartado vamos a crear  una base de datos denominada example_database y un usuario llamado example_user, pero 
puede sustituir estos nombres por valores diferentes

Lo que hago primero es establecer la conexión con la consola de MySQL usando la cuenta root

sudo mysql

<img width="533" height="240" alt="image" src="https://github.com/user-attachments/assets/4926100a-0800-4900-9121-7ff6d7c52478" />

Para crear una base de datos nueva, ejecuto el siguiente comando desde la consola de MySQL

mysql > CREATE DATABASE example_database;

<img width="285" height="76" alt="image" src="https://github.com/user-attachments/assets/d38468c3-63da-41cd-900d-cf0074dc2926" />

Ahora el siguiente comando crea un usuario nuevo llamado example_user, que utiliza mysql_native_password como método de autenticación 
predeterminado. Definimos la contraseña de este usuario como password, pero debe sustituir este valor por una contraseña segura de 
su elección.

mysql > CREATE USER 'example_user'@'%' IDENTIFIED BY 'Password_1';

<img width="455" height="62" alt="image" src="https://github.com/user-attachments/assets/61a9f5f3-31d5-4875-a265-e9747a525719" />

Ahora, le damos permiso a este usuario a la base de datos example_database:

mysql > GRANT ALL ON example_database.* TO 'example_user';

<img width="407" height="69" alt="image" src="https://github.com/user-attachments/assets/4179175e-6b88-4149-8bd1-df28ba32e51c" />

Esto proporcionará al usuario example_user privilegios completos sobre la base de datos example_database y, al mismo tiempo, 
evitará que este usuario cree o modifique otras bases de datos en su servidor.

Ahora, cierro el shell de MySQL con lo siguiente

mysql > exit

<img width="321" height="53" alt="image" src="https://github.com/user-attachments/assets/a38f4017-042d-4507-a355-0c7e1506fc5d" />

mysql -u example_user -p

<img width="558" height="229" alt="image" src="https://github.com/user-attachments/assets/1f0b9b19-07b9-46f3-97cd-fabde2f6b04e" />

Después de iniciar sesión en la consola de MySQL, confirmo que tenga acceso a la base de datos example_database

mysql > SHOW DATABASES;

<img width="155" height="25" alt="image" src="https://github.com/user-attachments/assets/bc80d85a-4505-4626-b9e4-b8541f387e66" />

Con esto se generará el siguiente resultado

<img width="170" height="155" alt="image" src="https://github.com/user-attachments/assets/a86ee9b4-f96f-4f12-8c73-c131a469e7cc" />

A continuación, crearemos una tabla de prueba denominada todo_list: Desde la consola de MySQL, ejecute la siguiente instrucción

mysql> CREATE TABLE example_database.todo_list (
mysql>          item_id INT AUTO_INCREMENT,
mysql>          content VARCHAR(255),
mysql>          PRIMARY KEY(item_id)
mysql> );

<img width="342" height="132" alt="image" src="https://github.com/user-attachments/assets/2f3d3e2f-1edd-4734-82be-1ab0208a9ea7" />

Ahora voy a insertar algunas filas de contenido en la tabla de prueba. Es posible que quiera repetir el siguiente comando algunas 
veces, usando valores diferentes

mysql > INSERT INTO example_database.todo_list (content) VALUES ("My first important item");

<img width="618" height="67" alt="image" src="https://github.com/user-attachments/assets/04f89005-4d01-4b30-ade6-f7a2b0116c35" />

Para confirmar que los datos se guardaron correctamente en su tabla, ejecute lo siguiente

mysql > SELECT * FROM example_database.todo_list;

<img width="333" height="26" alt="image" src="https://github.com/user-attachments/assets/7d8c483f-e1ee-42f2-a11e-fec1c7c9df97" />

Y aparece el siguiente resultado

<img width="267" height="128" alt="image" src="https://github.com/user-attachments/assets/78479927-d093-45ac-a017-8cd6bcba6038" />

Después de confirmar que haya datos válidos en la tabla de prueba, cierro la consola de MySQL

mysql > exit

<img width="327" height="49" alt="image" src="https://github.com/user-attachments/assets/c1d34133-b387-4515-a085-28562f6ee28a" />

Ahora, se podrá crear una secuencia de comandos PHP que se conecte a MySQL y realice consultas relacionadas con su contenido.
Para ello creo un nuevo archivo PHP en su directorio web root personalizado usando su editor preferido.

nano /var/www/your_domain/todo_list.php

<img width="584" height="18" alt="image" src="https://github.com/user-attachments/assets/17fe1dce-3499-4e2f-9b39-98fb802058c7" />

Ahora copio este contenido en la secuencia de comandos todo_listo.php

<img width="691" height="284" alt="image" src="https://github.com/user-attachments/assets/78047219-ea1b-4d6f-a3a3-896eb0cf7876" />

Ahora guardo y cierro el archivo cuando finalice la edición

Ahora me voy al navegador y escribo http://localhost/todo_list.php

