<h1>Practica 6</h1>

<b>services:</b> Define los servicios (contenedores) que se iniciarán en Docker. En este caso, tienes dos servicios: asir_bind9 y cliente.

Dentro del contenedor asir_bind9, tiene diferentes apartados.

<b>image:</b>  Indica que el contenedor utilizará la imagen ubuntu/bind9.

<b>platform:</b>  Define la plataforma (arquitectura) como linux/amd64, útil para especificar la compatibilidad del contenedor.

<b>ports:</b> - 54:54: Expone el puerto 54 del contenedor al puerto 54 del host, lo cual permite el acceso desde fuera del contenedor en ese puerto específico.

<b>networks: bind9_subnet</b> Conecta el contenedor a la red bind9_subnet.

<b>ipv4_address:</b> 172.28.5.1: Asigna al contenedor la dirección IP 172.28.5.1 en la red especificada.

<b>volumes:</b> Monta directorios del host en el contenedor.

Dentro del contenedor cliente, tiene diferentes apartados.

<b>tty:</b> true: Activa un terminal de texto interactivo para el contenedor, útil para trabajar en modo interactivo.

<b>stdin_open:</b> true: Mantiene el flujo de entrada estándar abierto para interactuar con el contenedor.

<b>dns:</b> - 172.28.5.1: Configura el servidor DNS del contenedor como 172.28.5.1, que es la dirección IP del contenedor asir_bind9.

<b>bind9_subnet:</b> Crea o utiliza una red llamada bind9_subnet.

<b>external:</b> true: Indica que esta red es externa (ya creada en Docker) y que Docker Compose no intentará crearla automáticamente.

Al usar el comando:

sudo docker compose up -d


Levantará los contenedores con todo lo que hemos configurado, y le ponemos el -d para que vaya en segundo plano. Luego usaremos el siguiente comando para entrar en la terminal del contenedor cliente.

docker exec -it cliente /bin/sh

Dentro del cliente hacemos un <u> apt update </u> y luego instalaremos dig.

apt install dnsutils

Para comprobar que esta instalado hacemos un: 

dig @172.25.5.1 ejemplo.asircastelao.inet

Asi veremos la interfaz de dig y que nos funciona.

