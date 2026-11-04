# Actividad #3

# Ejercicios

# Crea un directorio llamado "dir1" y otro llamado "dir2"

mkdir /var/www/html/dir1

mkdir /var/www/html/dir2

<img width="520" height="77" alt="image" src="https://github.com/user-attachments/assets/c23efea5-87bf-41ae-8c2b-9365bc381350" />

# Explica qué diferencia existe entre ambos y muestra su equivalencia con la directiva Require:

<Directory /var/www/example1>
Order Deny,Allow
Deny from All
Allow from 192.168.1.100
</Directory>

# Niega el acceso a todos excepto a 192.168.1.100

<Directory /var/www/example1>
Order Allow,Deny
Deny from All
Allow from 192.168.1.100
</Directory>

# Niega el acceso a todos

    
# Para dir1

# Permite el acceso de las peticiones provenientes de 10.3.0.100

<img width="576" height="37" alt="image" src="https://github.com/user-attachments/assets/d3befc88-b349-4467-92e9-911123346dee" />

<img width="213" height="51" alt="image" src="https://github.com/user-attachments/assets/b6f96f51-d7fc-41cf-b27d-152260e2706f" />

# Permite el acceso desde "marisma.intranet"

<img width="211" height="19" alt="image" src="https://github.com/user-attachments/assets/10573f21-0792-4091-8e60-208b02298d78" />

# Permite el acceso desde cualquier subdominio de "marisma.intranet"

<img width="207" height="21" alt="image" src="https://github.com/user-attachments/assets/46cbf8a4-0e11-40f2-bca8-3d76a9e19e31" />

# Permite el acceso de las peticiones provenientes de "10.3.0.100" con máscara "255.255.0.0"

<img width="236" height="20" alt="image" src="https://github.com/user-attachments/assets/c263b030-5108-4a87-ba92-5c4263c1bb7a" />

# Modifica la configuración de forma que el acceso a dir1:

# Se permita a "marisma.intranet" y no se permita desde 10.3.0.101"

<Directory /var/www/html/dir1>
	<RequireAll>
	Require host marisma.intranet
		Require not ip 10.3.0.101
	</RequireAll>
</Directory>

<img width="308" height="102" alt="image" src="https://github.com/user-attachments/assets/3230824a-f580-40ca-bac6-998925c03860" />

# Modifica la configuración de forma que el acceso a dir2:

# Se permita a "10.3.0.100/8" y no a "marisma.intranet"

<Directory /var/www/html/dir2>
	<RequireAll>
	Require ip 10.3.0.101/8
		Require not host marisma.intranet
	</RequireAll>
</Directory>

<img width="332" height="107" alt="image" src="https://github.com/user-attachments/assets/721a3d5b-fc4a-4145-9305-415f074f0802" />



