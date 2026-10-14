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



# 5. Crea un directorio “prueba” y otro directorio “prueba2”. Incluye un par de páginas en cada una de ellas.

# 6. Redirecciona el contenido de la carpeta “prueba” hacia “prueba2”

# 7. Es posible redireccionar tan solo una página en lugar de toda la carpeta. Pruébalo.

# 8. Usa la directiva userdir

# 9. Usa la directiva alias para redireccionar a una carpeta dentro del directorio de usuario.

# 10.¿Para qué sirve la directiva Options y dónde aparece. Comprueba si apache indexa los directorios. Si es así, ¿cómo lo desactivamos?
