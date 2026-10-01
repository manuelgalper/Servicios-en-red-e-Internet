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

<img width="528" height="215" alt="image" src="https://github.com/user-attachments/assets/21ea675b-67c6-4583-83ed-f197df943ed8" />
















