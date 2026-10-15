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



# 7. Es posible redireccionar tan solo una página en lugar de toda la carpeta. Pruébalo.

# 8. Usa la directiva userdir

# 9. Usa la directiva alias para redireccionar a una carpeta dentro del directorio de usuario.

# 10.¿Para qué sirve la directiva Options y dónde aparece. Comprueba si apache indexa los directorios. Si es así, ¿cómo lo desactivamos?
