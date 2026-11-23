# Actividad Virtualhost

Lee el artículo siguiente y lleva a cabo la práctica propuesta:

https://www.digitalocean.com/community/tutorials/como-configurar-virtual-host-de-apache-en-ubuntu-14-04-lts-es

# Paso Uno - Crear la Estructura del Directorio

En este primer paso lo que vamos a hacer es crear la estructura de directorios que mantendrán la información de nuestro sitio.
Los directorios los vamos a crear dentro de la ruta /var/www para los dos hosts virtuales que prevemos configurar. Dentro de
los dos directorios rearemos un directorio denominado public_htmlel cual mantendrá la información pública del sitio y sus 
respectivos archivos. Esto nos dará más flexibilidad en nuestro alojamiento.

Para crear los dos directorios lo haremos con los siguientes comandos:

sudo mkdir -p /var/www/ejemplo.com/public_html

sudo mkdir -p /var/www/pruebas.com/public_html

<img width="628" height="72" alt="image" src="https://github.com/user-attachments/assets/42c08cd2-db7c-40bc-bd03-294e46c233d4" />

# Paso Dos - Otorgar Permisos

Una vez creado los dos directorios vamos a cambiar el propietario otorgando los permisos haciendo lo siguiente

sudo chown -R $USER:$USER /var/www/ejemplo.com/public_html

sudo chown -R $USER:$USER /var/www/pruebas.com/public_html

