# Actividad 0.2 - UDP and TCP: Comparison of Transport Protocols

# Diferencias entre udp y tcp? (min 2:46 y 4:15)

El protocolo TCP garantiza una entrega de datos segura y ordenada a costa de ser más lento, mientras que el protocolo UDP prioriza la velocidad máxima sin importar si se pierden algunos paquetes.

# ¿Qué aplicaciones usan tcp?

http, smtp, pop, imap, ssh

# ¿Qué aplicaciones usan udp?

DNS (resolución de nombres, también usa TCP para consultas grandes).

DHCP (asignación dinámica de IPs).

VoIP (llamadas de voz por internet) y videollamadas.

Streaming de video en vivo.

Juegos en línea rápidos.

# ¿Qué capa almacena el puerto?

La capa de transporte

# ¿Qué capa almacena la dirección IP?

La capa de red

# ¿Qué es three-way handshake?

Es el proceso de establecimiento de conexión de tres pasos que usa TCP antes de enviar datos reales.

SYN: El cliente envía un paquete de sincronización al servidor.

SYN-ACK: El servidor responde aceptando la sincronización.

ACK: El cliente confirma la respuesta del servidor y la conexión queda abierta para transmitir datos.
