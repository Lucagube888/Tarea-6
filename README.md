<h1>Práctica 6</h1>

<b>services:</b> Define os servizos (contenedores) que se iniciarán en Docker. Neste caso, tes dous servizos: asir_bind9 e cliente.

Dentro do contedor asir_bind9, ten diferentes apartados.

<b>image:</b> Indica que o contedor empregará a imaxe ubuntu/bind9.

<b>platform:</b> Define a plataforma (arquitectura) como linux/amd64, útil para especificar a compatibilidade do contedor.

<b>ports:</b> - 54:54: Expón o porto 54 do contedor ao porto 54 do host, o cal permite o acceso dende fóra do contedor nese porto específico.

<b>networks: bind9_subnet</b> Conecta o contedor á rede bind9_subnet.

<b>ipv4_address:</b> 172.28.5.1: Asigna ao contedor o enderezo IP 172.28.5.1 na rede especificada.

<b>volumes:</b> Monta directorios do host no contedor.

Dentro do contedor cliente, ten diferentes apartados.

<b>tty:</b> true: Activa un terminal de texto interactivo para o contedor, útil para traballar en modo interactivo.

<b>stdin_open:</b> true: Mantén o fluxo de entrada estándar aberto para interactuar co contedor.

<b>dns:</b> - 172.28.5.1: Configura o servidor DNS do contedor como 172.28.5.1, que é o enderezo IP do contedor asir_bind9.

<b>bind9_subnet:</b> Crea ou utiliza unha rede chamada bind9_subnet.

<b>external:</b> true: Indica que esta rede é externa (xa creada en Docker) e que Docker Compose non intentará creala automaticamente.

Ao usar o comando:

    sudo docker compose up -d

Levantará os contedores con todo o que configuramos, e poñémoslle o -d para que vaia en segundo plano. Logo empregaremos o seguinte comando para entrar no terminal do contedor cliente.

    docker exec -it cliente /bin/sh

Dentro do cliente facemos un <u>apt update</u> e logo instalaremos dig.

    apt install dnsutils

Para comprobar que está instalado facemos un: 

    dig @172.25.5.1 exemplo.asircastelao.inet

Así veremos a interface de dig e que nos funciona.

