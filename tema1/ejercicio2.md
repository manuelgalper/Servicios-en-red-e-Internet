# Configuración básica de Apache

# Actividad #2.1

Pon en marcha el servidor Apache y lleva a cabo los siguientes cambios en el archivo de configuración

# 1. Apache utilizará el puerto 81 además del 80

Vamos a hacer que Apache utilice el puerto 81 además del 80, lo que hago primero es ir al directorio 
/etc/apache2 con el siguiente comando:

cd /etc/apache2 

<img width="414" height="19" alt="image" src="https://github.com/user-attachments/assets/867dca26-bf67-42b6-89b3-d55b00d4566f" />

Y una vez entrado en el directorio escribo ls

<img width="513" height="67" alt="image" src="https://github.com/user-attachments/assets/1525bd5d-af9d-4138-84b6-c72deb448821" />

Ahora una vez que estoy en el directorio /etc/apache2 edito el fichero de puertos con el siguiente comando

sudo nano /etc/apache2/ports.conf

<img width="615" height="21" alt="image" src="https://github.com/user-attachments/assets/cb9f1cb8-2b7b-48ba-89a8-639d3528ae2c" />

Y una vez entrado en el fichero ports.conf debajo del Listen 80 escribo Listen 81

<img width="699" height="232" alt="image" src="https://github.com/user-attachments/assets/3788e549-0ebd-482f-9217-89243db5df08" />

Ahora compruebo la configuración y reinicio apache

sudo apache2ctl configtest
sudo systemctl restart apache2

<img width="801" height="110" alt="image" src="https://github.com/user-attachments/assets/223f5675-e025-4463-ba5d-2e1acf6d4a00" />

Ahora me voy al navegador y escribo http://localhost:81, y vemos que apache responde

<img width="1013" height="611" alt="image" src="https://github.com/user-attachments/assets/7fc82f2e-7aae-4dd3-9671-d03e7e4dd8b2" />

# 2. Añadir el dominio “marisma.intranet” en el fichero “hosts”

Ahora lo siguiente es añadir el dominio "marisma.intranet" en el fichero hosts, para ello edito el fichero /etc/hosts lo hago con
el siguiente comando

sudo nano /etc/hosts

<img width="455" height="19" alt="image" src="https://github.com/user-attachments/assets/6d5b3f76-05e2-4782-8d9f-49938102c435" />

Ahora una vez que estoy dentro del fichero /etc/hosts añado la línea 127.0.0.1 marisma.intranet

<img width="804" height="369" alt="image" src="https://github.com/user-attachments/assets/2e3cdf9c-f536-481d-94c1-2f74847b3597" />

Y ahora lo que hago es comprobar la resolución del nombre para ello escribo el siguiente comando

getent hosts marisma.intranet

Y vemos que aparece la 12.0.0.1 marisma.intranet

<img width="512" height="50" alt="image" src="https://github.com/user-attachments/assets/152402d8-7d9c-4dbc-bb2e-6f63224fd23b" />

Por último en el navegador pongo http://marisma.intranet y vemos que apache responde

<img width="1013" height="607" alt="image" src="https://github.com/user-attachments/assets/48ae0a1a-be6b-4b23-adfc-c609dfb168b3" />

# 3. Cambia la directiva “ServerTokens” para mostrar el nombre del producto.

En el siguiente apartado vamos a cambiar la directiva "ServerTokens" para mostrar el nombre del producto, para ello edito el fichero
sudo nano /etc/apache2/conf-available/security.conf

<img width="671" height="20" alt="image" src="https://github.com/user-attachments/assets/d6a784b6-edf6-4e2c-ba33-35d891158830" />

Una vez que estoy dentro del fichero sudo nano /etc/apache2/conf-available/security.conf busco la directiva ServerTokens y establezco
ServerTokens ProductOnly

<img width="801" height="329" alt="image" src="https://github.com/user-attachments/assets/348bd026-2cec-44e5-9edf-3955e7a0fe42" />

Ahora aplico los siguiente cambios

sudo apache2ctl configtest
sudo systemctl reload apache2

<img width="798" height="92" alt="image" src="https://github.com/user-attachments/assets/1f831aac-dabd-4370-bbc2-9809000fcdef" />

# 4. Comprueba si se visualiza el pie de página en las páginas generadas por Apache (por ejemplo, en las páginas de error). Cambia el valor de la directiva “ServerSignature” y comprueba que funciona correctamente.

Lo siguiente que vamos a hacer es comprobar si se visualiza el pie de página en las páginas de Apache, para ello abro el fichero

sudo nano /etc/apache2/conf-available/security.conf

<img width="663" height="20" alt="image" src="https://github.com/user-attachments/assets/06c0d6fa-5960-4df5-94aa-aab28ff7ba93" />

Y una vez entrado en el fichero sudo nano /etc/apache2/conf-available/security.conf vemos que se visualiza 

<img width="801" height="297" alt="image" src="https://github.com/user-attachments/assets/804e9fd1-2c26-48c4-8b5e-74ab40812d00" />

Ahora reinicio apache con el comando sudo systemctl reload apache2

<img width="516" height="19" alt="image" src="https://github.com/user-attachments/assets/369f1f6a-b8b8-4632-a602-e436ce002841" />

Para comprobarlo me voy al navegador y escribo una página inexistente como por ejemplo http://localhost/error404 y vemos que la 
directiva funciona correctamente ya que al provocar el error NotFound(404) ahora aparece la línea de pie de página que dice Apache 
Server at localhost Port 80

<img width="1012" height="568" alt="image" src="https://github.com/user-attachments/assets/7ed77d6e-2990-45e7-aeec-1156ad154e46" />

Ahora para cambiar el valor de la directiva “ServerSignature” y comprueba que funciona correctamente, lo primero que hago es volver
a abrir el archivo de configuración sudo nano /etc/apache2/conf-available/security.conf

<img width="660" height="19" alt="image" src="https://github.com/user-attachments/assets/aa0ba69e-c03a-4ce1-a6d6-099edb975a6d" />

Ahora modifico la directiva cambiando el valor de On a Off

<img width="802" height="324" alt="image" src="https://github.com/user-attachments/assets/f320c989-1c3b-4507-a5b6-b54b3b69a0ec" />

Luego reinicio Apache para aplicar los cambios en el servidor

sudo systemctl restart apache2

<img width="510" height="22" alt="image" src="https://github.com/user-attachments/assets/04a1e743-12bf-42f4-af1e-62505801fdc7" />

Ahora vuelvo al navegador y compruebo el resultado, y vemos que en la imagen se puede ver claramente que el cambio a ServerSignature Off 
ha funcionado correctamente.

<img width="1013" height="572" alt="image" src="https://github.com/user-attachments/assets/ef99fbaa-ca06-4031-ad09-1cd7d0fb3b5e" />

# 5. Crea un directorio “prueba” y otro directorio “prueba2”. Incluye un par de páginas en cada una de ellas.

En este apartado vamos a crear dos directorios, uno que se va a llamar prueba y otro que se va a llamar prueba2, para crear estos
dos directorios escribo lo siguiente

sudo mkdir -p /var/www/html/prueba
sudo mkdir -p /var/www/html/prueba2

<img width="558" height="31" alt="image" src="https://github.com/user-attachments/assets/166d84dc-7297-4d93-9d9d-f0f65b7bfd1c" />

Ahora voy a incluir un par de páginas en el directorio prueba, para ello escribo el siguiente comando

sudo nano /var/www/html/prueba/index.html

<img width="599" height="21" alt="image" src="https://github.com/user-attachments/assets/16793bee-4a48-496f-993e-eb264fcf5952" />

<img width="802" height="225" alt="image" src="https://github.com/user-attachments/assets/eda369ab-6ac5-42c9-bfb8-529ac199b743" />

Ahora creo la segunda

sudo nano /var/www/html/prueba/pagina2.html

<img width="608" height="22" alt="image" src="https://github.com/user-attachments/assets/b38f0a4d-dd58-4da0-967a-2a0d5f5fc81d" />

<img width="802" height="213" alt="image" src="https://github.com/user-attachments/assets/4c7d83dc-62eb-4a92-a89e-918d5e9eb648" />

Ahora hago lo mismo en prueba2

Y ahora compruebo que puedo acceder a las cuatro páginas

<img width="1014" height="573" alt="image" src="https://github.com/user-attachments/assets/2d8df314-a52e-41b2-ab5a-6dfb6e58c456" />

<img width="1013" height="573" alt="image" src="https://github.com/user-attachments/assets/13579235-20b5-47b1-b086-63d9427b9743" />

<img width="1013" height="576" alt="image" src="https://github.com/user-attachments/assets/9b20f0e0-bdb6-47f3-8c95-eace62e3d037" />

<img width="1011" height="572" alt="image" src="https://github.com/user-attachments/assets/31c156b4-54f2-46c0-949d-3e3e729edd2f" />

# 6. Redirecciona el contenido de la carpeta “prueba” hacia “prueba2”

En este apartado vamos a ver como redireccionar el contenido de la carpeta "prueba" hacia "prueba2", para ello compruebo que el módulo
está habilitado

sudo a2enmod alias

<img width="450" height="78" alt="image" src="https://github.com/user-attachments/assets/754722d5-449f-4a22-8ae1-4d21ffb9bf94" />

Ahora edito el archivo de configuración del sitio

sudo nano /etc/apache2/sites-available/000-default.conf

<img width="690" height="23" alt="image" src="https://github.com/user-attachments/assets/6ae25ef9-0477-462c-ad5d-663a02ddd6a3" />

Luego dentro de un bloque <VirtualHost>, añado Redirect permanent /prueba/ /prueba2/

<img width="799" height="292" alt="image" src="https://github.com/user-attachments/assets/b060b928-c756-4240-bba5-6ac053671c7b" />

Ahora valido y reiniciamos el servidor

sudo apache2ctl configtest
sudo systemctl reload apache2

<img width="798" height="109" alt="image" src="https://github.com/user-attachments/assets/745a0e1f-820f-4dfe-a0fd-47d71e37d889" />

Ahora me voy al navegador y escribo http://localhost/prueba/ y vemos que la redirección se ha completado con éxito, ya que se ha 
visualizando correctamente el contenido de la carpeta destino con el mensaje "Primera página de prueba2".

# 7. Es posible redireccionar tan solo una página en lugar de toda la carpeta. Pruébalo.

Sí, se puede redireccionar únicamente una página. Me vuelvo archivo de configuración del sitio

sudo nano /etc/apache2/sites-available/000-default.conf

<img width="690" height="24" alt="image" src="https://github.com/user-attachments/assets/7ad5b6c0-0b09-4998-b074-efba74dca28f" />

Ahora añado una regla específica como por ejemplo Redirect permanent /prueba/pagina2.html /prueba2/pagina2.html

<img width="798" height="294" alt="image" src="https://github.com/user-attachments/assets/2bf981fe-8cd3-4b67-9f04-6b913b8bfff6" />

Ahora valido y recargo apache

sudo apache2ctl configtest
sudo systemctl reload apache2

<img width="802" height="93" alt="image" src="https://github.com/user-attachments/assets/d948db5b-dc52-470b-bb2a-ee4e89978766" />

Ahora compruebo ambas rutas

http://localhost/prueba/pagina2.html debe redirigir a /prueba2/pagina2.html.
http://localhost/prueba/ debe seguir mostrando la página de prueba.

<img width="1015" height="570" alt="image" src="https://github.com/user-attachments/assets/1462c04e-46ec-4079-aa25-f787c8d4d052" />

<img width="1013" height="572" alt="image" src="https://github.com/user-attachments/assets/8f87552d-4509-4b8b-9603-21ea475eb66b" />

# 8. Usa la directiva userdir

Para usar la directiva userdir en linux lo primero que hago es ejecutarla con permisos de administrador (sudo), lo hago con el
comando 

sudo a2enmod userdir

<img width="459" height="78" alt="image" src="https://github.com/user-attachments/assets/63dbc43a-df27-4013-92b4-e4e8a792ac9d" />

Ahora una vez que haya ejecutado la directiva userdir voy a crear una carpeta web llamada public_html, lo hago con el siguiente 
comando

mkdir /home/manuel/public_html

<img width="519" height="20" alt="image" src="https://github.com/user-attachments/assets/b1d90296-eb3c-45ae-9fb8-561c4c1b08c5" />

Ahora creamos el archivo index.html dentro de la carpeta correcta que acabamos de generar

nano /home/manuel/public_html/index.html

<img width="631" height="19" alt="image" src="https://github.com/user-attachments/assets/8b3fd35c-1b15-468f-b233-3fc0282f4356" />

<img width="285" height="159" alt="image" src="https://github.com/user-attachments/assets/d2ab8544-0744-4eff-bdbd-0352509eed79" />

Luego le aplico los permisos correspondientes para que Apache pueda leer el home y la nueva carpeta

<img width="555" height="34" alt="image" src="https://github.com/user-attachments/assets/7e4d492b-b6ea-496d-a372-9b2054e5ef78" />


# 9. Usa la directiva alias para redireccionar a una carpeta dentro del directorio de usuario.

Vamos a usar la directiva para redireccionar a una carpeta dentro del directorio de usuario, para ello abro el archivo de configuración

sudo nano /etc/apache2/sites-available/000-default.conf

<img width="684" height="18" alt="image" src="https://github.com/user-attachments/assets/c994b112-3768-4812-ab38-13eb2a94f893" />

Ahora añado el alias y sus permisos

<img width="468" height="164" alt="image" src="https://github.com/user-attachments/assets/d5d0c3bc-d423-4d8b-891c-0ada0cb5c783" />

Ahora creo la carpeta de prueba

mkdir -p /home/manuel/carpeta_privada

<img width="563" height="37" alt="image" src="https://github.com/user-attachments/assets/36c58632-7b5e-468b-9226-94ded7eb8fd9" />

Ahora dentro de la carpeta privada creo el archivo index.html lo hago con el siguiente comando

nano /home/manuel/carpeta_privada/index.html

<img width="617" height="23" alt="image" src="https://github.com/user-attachments/assets/10278b68-6769-4b5c-99bc-df81ca2cb2e7" />

<img width="803" height="334" alt="image" src="https://github.com/user-attachments/assets/344aadb1-8738-4462-913b-72f6f6300b3f" />

Ahora doy permisos de lectura y ejecución para que Apache pueda acceder lo hago con los siguientes comandos

chmod 755 /home/manuel
chmod 755 /home/manuel/carpeta_privada

<img width="587" height="35" alt="image" src="https://github.com/user-attachments/assets/ff1b2709-500a-4734-aff6-7d2b4ec1b673" />

Una vez dado los permisos, guardo, valido y reinicio Apache

sudo apache2ctl configtest
sudo systemctl restart apache2

<img width="797" height="110" alt="image" src="https://github.com/user-attachments/assets/a1372b48-054b-4007-aabd-b2b73ffb4bda" />

Ahora me voy al navegador y pongo http://localhost/micarpeta y vemos que alias funciona correctamente

<img width="1012" height="572" alt="image" src="https://github.com/user-attachments/assets/69e2e9f1-efff-420b-9240-625081d2bd8d" />

# 10.¿Para qué sirve la directiva Options y dónde aparece. Comprueba si apache indexa los directorios. Si es así, ¿cómo lo desactivamos?

Controla qué características y funciones del servidor están disponibles en un directorio específico (por ejemplo, si se permite listar 
archivos, seguir enlaces simbólicos o ejecutar scripts CGI).

Aparece dentro de los bloques <Directory> en los archivos de configuración de sitios (sites-available/*), en el archivo general apache2.conf,
o en archivos locales .htaccess.

# Comprobar si Apache indexa los directorios

Por defecto, si entras a una carpeta de tu servidor que no tiene un archivo index.html o index.php, Apache listará de forma automática todos 
los archivos y subcarpetas que contenga. Esto se conoce como indexación automática (un listado visual tipo explorador de archivos).

# ¿Cómo lo desactivamos?

Para desactivarlo lo primero que hago es modificar la directiva Options dentro del bloque <Directory> correspondiente en el archivo de configuración,
ambiando el parámetro Indexes por -Indexes (añadiendo un signo menos) lo hago con el comando sudo nano /etc/apache2/sites-available/000-default.conf

<img width="690" height="20" alt="image" src="https://github.com/user-attachments/assets/a4f90000-4580-43fd-862a-8bd3baef7397" />

<img width="456" height="168" alt="image" src="https://github.com/user-attachments/assets/9c30dab3-c0fb-452c-89d7-dd3348951fd9" />

Ahora guardo y reinicio apache

sudo apache2ctl configtest
sudo systemctl restart apache2

<img width="803" height="91" alt="image" src="https://github.com/user-attachments/assets/10d102c0-6f89-4b76-b59b-563507d23bda" />



