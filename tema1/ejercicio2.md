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



# 3. Cambia la directiva “ServerTokens” para mostrar el nombre del producto.

# 4. Comprueba si se visualiza el pie de página en las páginas generadas por Apache (por ejemplo, en las páginas de error). Cambia el valor de la directiva “ServerSignature” y comprueba que funciona correctamente.

# 5. Crea un directorio “prueba” y otro directorio “prueba2”. Incluye un par de páginas en cada una de ellas.

# 6. Redirecciona el contenido de la carpeta “prueba” hacia “prueba2”

# 7. Es posible redireccionar tan solo una página en lugar de toda la carpeta. Pruébalo.

# 8. Usa la directiva userdir

# 9. Usa la directiva alias para redireccionar a una carpeta dentro del directorio de usuario.

# 10.¿Para qué sirve la directiva Options y dónde aparece. Comprueba si apache indexa los directorios. Si es así, ¿cómo lo desactivamos?
