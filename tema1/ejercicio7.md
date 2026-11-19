# Lleva a cabo los ejercicios propuestos en el siguiente enlace
http://www.josedomingo.org/pledin/2011/10/ejemplos-del-modulo-rewrite-en-apache-2-2/

# Siguiendo las técnicas anteriormente vistas, realiza una reescritura de URL para que pudiéramos realizar búsquedas con URL de la siguiente manera:

http://localhost/buscar/hola.html

Primero abro el terminal, activo el módulo rewrite y reinicio apache

sudo a2enmod rewrite

sudo systemctl restart apache2

<img width="514" height="113" alt="image" src="https://github.com/user-attachments/assets/47a7db18-2687-4cd0-95ab-f3693f845a6b" />

Ahora abro el archivo de configuración de Apache

sudo nano /etc/apache2/apache2.conf

<img width="556" height="20" alt="image" src="https://github.com/user-attachments/assets/f028f492-ed17-449f-b965-bd0e8bcd5012" />

Busco el bloque <Directory /var/www/> y Cambia AllowOverride None por AllowOverride All

<img width="269" height="85" alt="image" src="https://github.com/user-attachments/assets/8abcc434-fb16-4b42-bfbd-43a0e395ec04" />

Lo guardo y reinicio apache

sudo systemctl restart apache2

<img width="518" height="21" alt="image" src="https://github.com/user-attachments/assets/30eeba69-3e73-4f98-abb4-69a71c7e1e9a" />

Luego coloco el código en el directorio raíz de nuestro servidor web (/var/www/html/)

sudo nano /var/www/html/.htaccess

<img width="536" height="20" alt="image" src="https://github.com/user-attachments/assets/fc1f31fc-e43e-4871-86dd-f92eb00df20d" />

<img width="799" height="311" alt="image" src="https://github.com/user-attachments/assets/74db42d1-ccf4-462e-b2b1-ab831eb8101b" />

Por último en el navegador escribo http://localhost/buscar/hola.html y vemos que al entrar Apache reescribe la URL internamente y 
PHP devuelve Resultado de búsqueda para: hola.

<img width="1014" height="607" alt="image" src="https://github.com/user-attachments/assets/a041d630-4342-4ab9-ade1-d67b2931121a" />


# Realiza un .htaccess para evitar el hot-linking. Puedes usar esta esta imagen para realizar el ejercicio.





