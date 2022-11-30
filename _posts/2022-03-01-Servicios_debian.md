---
layout: single
title: Servicios DHCP,DNS,APACHE,SHH,VNC,FTP bajo Debian 11
excerpt: "Practica de servicios en red curso 2021/2022 , en esta se desarolla un escenario con una red local en la que se implantan los servicios NAT ,DNS , DHCP , SSH, VNC , SMTP ,POP3 , IMAP ,FTP"
date: 2022-03-01
classes: wide
header:
  teaser: /assets/images/prueba/logo.png
  teaser_home_page: true
  icon: /assets/images/logo.jpg
categories:
  - Servicios
tags:
  - SMR
---
<!-- Google tag (gtag.js) -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-GVDYVWJLRH"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());

  gtag('config', 'G-GVDYVWJLRH');
</script>









1. # **NAT con iptables**
   1. ## **Instalación del entorno de pruebas**
Vamos a instalar el siguiente entorno:

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.001.png)
1. ## **Configuración de VirtualBox**
Servidor debian :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.002.png)

Cliente windows

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.003.png)
![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.004.png)

Cliente debian

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.005.png)
![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.006.png)




1. # **Configuración de red**
Lo primero que haremos sera configurar las tarjetas de red de nuestras maquinas .

1. ### **Servidor debian :**
Editamos el fichero con nano /ect/network/interfaces como superusuario y añadimos las siguientes lineas .

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.007.png)

Los cuadros rojos corresponden a la configuración de las tarjetas de red enp0s3(tarjeta externa) y enp0s8(red interna). El cuadro azul corresponde a las reglas iptables para permitir las peticiones al exterior y prohibir las interiores .
1. ### **Cliente debian :**
Editamos el fichero con nano /etc/network/interfaces como superusuario y añadimos las siguientes lineas .La puerta de enlace sera la dirección ip de la tarjeta del servidor interna .

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.008.png)


1. ### **Cliente Windows 10 :**
En windows 10 configuramos manualmente accediendo a conexiones de red > configuracion del adaptador > ipv4 y le asignamos lo siguiente .Al igual que el cliente debian cambiando la dirección ip . He puesto dns de Google porque utilizo mi red movil .

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.009.png)























1. ## **Configuración del servidor**
Modificar el fichero /etc/sysctl.conf. Hay que descomentar la línea :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.010.png)

Comprobamos si se ha aplicado

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.011.png)


1. ## **Comprobación de internet en los clientes**
Windows 10

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.012.png)

Debian 11

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.013.png)




# **DHCP**
1. ## **Instalación del servidor isc-dhcp-server**
Para instalar nuestro servidor dhcp ejecutamos:

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.015.png)

Nos dará el siguiente error ya que no esta configurado :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.016.png)





1. ## **Configuración del servidor isc-dhcp-server**

Lo primero que tenemos que hacer es configurar el interfaz de red por el que va a trabajar el servidor dhcp, para ello editamos el siguiente fichero:

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.017.png)

Y añadimos nuestra interfaz que repartirá direcciones :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.018.png)

Configura el servidor dhcp con las siguientes características:

- Rango de direcciones a repartir: 192.168.0.100 - 192.168.0.110
- Máscara de red: 255.255.255.0
- Duración de la concesión: 1 hora
- Puerta de enlace: 192.168.0.1
- Servidores DNS: 8.8.8.8

Para ello editamos el siguiente archivo :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.019.png)




Ahora añadimos lo siguiente :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.020.png)

Aquí estamos configurando nuestro ámbito conforme al enunciado .

Ahora deberemos de reiniciar el servicio con el siguiente comando :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.021.png)
1. ## **Configura los clientes para obtener un direccionamiento dinámico**
Editaremos la configuración de red para que use el dhcp :

En el debian editamos el network/interfaces:

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.022.png)


Ahora reiniciamos la tarjeta de red :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.023.png)

Ahora comprobaremos si nos a asignado ip con ipconfig:

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.024.png)

Vemos que se ha asignado correctamente . Repetiremos lo mismo con nuestro cliente windows .

Configuramos la tarjeta de red para que utilice el protocolo dhcp, reiniciamos la tarjeta  y comprobamos la ip que nos ha asignado :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.025.png)

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.026.png)







Ahora vamos a comprobar las concesiones de direcciones para ello deberemos ver el siguiente archivo . Lo abriremos con cat ya que es importante no editarlo ,  puede causar problemas .

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.027.png)

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.028.png)







1. ## **Reserva en un servidor dhcp**
Para ello deberemos editar el archivo de configuración de nuestro servidor dhcp :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.029.png)

Una vez aquí vamos a añadir las siguientes lineas :

- Nombre de la reserva
- hardware Ethernet: Es la dirección MAC de la tarjeta de red del host.
- fixed-address: La dirección IP que le vamos a asignar.

Quedaría nuestra reserva así(la pondremos fuera de la configuración de nuestro ámbito):

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.030.png)

Ahora reiniciaremos el servicio

Vamos a comprobar que se ha realizado la concesión , para ello nos vamos a windows . Es posible que tengamos que renovar la concesión o reiniciar la tarjeta de red .

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.031.png)

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.032.png)



Vamos a comprobar qué ocurre con la configuración de los clientes en determinadas circunstancias, para ello vamos a poner un tiempo de concesión muy bajo . Le pondré 1 min .

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.033.png)

1.Los clientes toman una configuración, y a continuación apagamos el servidor dhcp. ¿Qué ocurre con el cliente windows? ¿Y con el cliente Linux?

En windows nos asignara una dirección de APIPA

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.034.png)

Mientras que en Linux no me asigna ninguna dirección ip , aunque después me asigno una dirección de APIPA

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.035.png)






2.Los clientes toman una configuración, y a continuación cambiamos la configuración del servidor dhcp (por ejemplo, el rango). ¿Qué ocurre con el cliente windows? ¿Y con el cliente Linux?

Modificamos el rango :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.036.png)

Y reiniciamos el servicio

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.037.png)

Con windows mantengo la dirección de la reserva   :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.038.png)

Y con Linux nos asigna la dirección del nuevo rango  :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.039.png)











1. ## **Actividad de ampliación**
Realizar las modificaciones necesarias en la configuración actual de nuestro servidor dhcp para que reparta direcciones ip a dos redes diferentes, la 192.168.0.0 y la 192.168.2.0.

Lo primero que haremos sera añadir una cuarta tarjeta de red  y la configuraremos manualmente . Si no sabemos el nombre de la interfaz podemos verlo con ip a :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.040.png)

Ahora la configuraremos estática  , siguiendo el enunciado y la añadimos al /etc/default/isc-dhcp-server.

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.041.png)

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.042.png)

Y configuramos nuestro segundo rango :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.043.png)

Ahora reiniciamos el servicio :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.044.png)





Ahora le añadiré varias tarjetas de red a mi cliente para comprobar las concesiones y configuramos las tarjetas  :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.045.png)

Y nos habría concedido dirección ip en ambos rangos :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.046.png)




# **DNS**
1. ## **Dnsmasq**
El paquete dnsmasq permite poner en marcha un servidor DNS de una forma muy sencilla. Simplemente instalando y arrancando el servicio dnsmasq, sin realizar ningún tipo de configuración adicional, nuestro PC se convertirá en un servidor caché DNS y además, resolverá los nombres que tengamos configurados en el archivo /etc/hosts de nuestro servidor. La resolución funcionará tanto en sentido directo como en sentido inverso, es decir, resolverá la IP dado un nombre de PC y el nombre del PC dada la IP.
1. ### **Instalación**
Para instalarlo solo sera necesario introducir el siguiente comando :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.048.png)
1. ### **Configuración**
A continuación, editamos el fichero /etc/dnsmasq.conf y modificamos las siguientes líneas:

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.049.png)

1. Descomentamos strict-order para que se realicen las peticiones DNS a los servidores que aparecen en el fichero /etc/resolv.conf en el orden en él aparecen.

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.050.png)

1. Incluimos las interfaces de red que deben aceptar peticiones DNS, descomentar la línea interface por ejemplo: interface=eth0

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.051.png)

Ahora crearemos nuestro archivo de configuración :

1. Creamos el fichero de configuración de nuestra zona :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.052.png)

1. El dominio que hemos elegido es iesgn.org

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.053.png)

1. Suponemos que el nombre del servidor es miservidor.

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.054.png)

1. Vamos a suponer que tenemos un servidor ftp que se llame ftp.iesgn.org y que está en 192.168.1.201 (esto es ficticio) y que tenemos dos sitios webs: www.iesgn.org y departamentos.iesgn.org.

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.055.png)

1. ` `Además queremos nombrar al cliente que tenía asignada una reserva: lisa.

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.056.png)

1. Y reiniciamos el servicio

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.057.png)






1. ### **Ejercicios**
1.Configura los clientes e indica que su DNS es nuestro servidor. Si tienes un servidor DHCP modificarlo para que envíe el nuevo DNS a los clientes.

Editamos el fichero :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.058.png)

Y reiniciamos el servicio :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.059.png)

Ahora comprobaremos si el cliente nos ha cambiado el dns mirando el siguiente archivo :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.060.png)

Se nos ha cambiado satisfactoriamente .

2.Comprueba el funcionamiento usando el comando dig/nslookup desde los clientes preguntando por los distintos nombres. Comprueba que el servidor DNS hace de forwarder preguntando con  dig/nslookup la dirección ip de www.josedomingo.org.

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.061.png)

Para la pagina de Jose domingo la respuesta es no autorizada porque nuestro servidor no tiene la resolución en su fichero y tiene que utilizar un forwarder

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.062.png)



Como ves arriba yo he creado mi propia zona y a pesar de haber seguido los pasos de esta [pagina](https://www.josedomingo.org/pledin/2020/12/servidor-dns-dnsmasq/) de Jose domingo , no he conseguido que las respuestas estén autorizadas .

He creado el archivo dns.conf .

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.063.png)

Y he creado  mi zona :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.064.png)

También he probado mas cosas sin embargo la única forma que he conseguido que me de respuesta autorizada es teniendo solo las resoluciones en el fichero host del servidor , sin crear mi zona .











1. ## **DNS BIND 9**
   1. ### **Instalación**
Lo primero que haremos sera desinstalar dnsmasq ya que ambos no son compatibles :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.065.png)

Ademas podemos ver que nos dice que el directorio /etc/dnsmasq.d/ al no estar vació no se ha borrado seria bueno que lo borrásemos manualmente para eliminar todo rastro de anteriores configuraciones :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.066.png)


Ahora vamos a instalarlos bind:
1. ### **Configuración**

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.067.png)


Ahora vamos a editar el fichero  /etc/bind/named.conf.local donde crearemos las zonas (directas e inversas). En el caso de la práctica nos piden una directa (isgn.com) y otra inversa (red 192.168.1). 

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.068.png)

Añadiremos las siguientes líneas a dicho fichero :

En el directorio / etc/bind están los ficheros db.empty y db.127 (ficheros de configuración de la zona directa e inversa respectivamente). Los copiamos al directorio / var/cache/bind para empezar a añadir los registros

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.069.png)

Modificamos el fichero  / var/cache/bind/db.isgn e incluimos las siguientes líneas para la resolución directa :

-javiercruces es el nombre de mi maquina lo he cambiado para facilitar las cosas

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.070.png)

Ahora haremos lo mismo para la resolución inversa :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.071.png)

Ahora reiniciaremos el servicio para que se apliquen los cambios :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.072.png)

Ademas para asegurarnos de que hemos realizado bien la configuración vamos a mirar el estado del servicio para ver si nuestras zonas están funcionando :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.073.png)

Este paso es opcional , pero gracias a revisar esto he descubierto porque no me hacia la resolución inversa y gracias a ver las zonas que estaban cargadas me di cuenta de que el error estaba en el fichero de configuración /etc/bind/named.conf.local y pude solucionarlo .
1. ### **Reenviador**
Hasta ahora, sólo nos resolvería los nombres e ip de nuestra red local. Si queremos configurar un reenviador al que preguntar en caso de que el DNS local no pueda darnos la respuesta, debemos editar el fichero nano / etc/bind/named.conf.options y añadir lo siguiente:

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.074.png)

Antes de hacer este apartado aclarar que como en el apartado de dnsmasq ya comentamos el fichero host y modificamos la configuración del dhcp para que asigne el dns automáticamente , lo omitiré de esta parte
1. ### **Ejercicios**
Comprueba el funcionamiento usando el comando dig/nslookup desde los clientes preguntando por los distintos nombres. Comprueba que el servidor DNS hace de forwarder preguntando con  dig/nslookup la dirección ip de www.josedomingo.org .

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.075.png)

Vemos aquí que las respuestas son correctas , las que están en nuestro servidor estas autorizadas mientras que la pagina de Jose domingo nos la ha echo un forwarder .







Ahora haré las mismas peticiones pero inversas :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.076.png)
![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.077.png)

Con esto hemos comprobado que el servidor dns funciona correctamente .


![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.078.png)


1. # **SSH**
## **Práctica  1: Gestión remota usando SSH**
Lo primeros que deberemos de hacer sera instalarnos el paquete  en el servidor y el cliente :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.079.png)

Por seguridad se suele no permitir la conexión del root al servidor; para ello, se debe modificar el archivo /etc/ssh/sshd\_config, y se pone la siguiente opción:


![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.080.png)




Y reiniciamos el servicio para que se apliquen los cambios :
1. ### **Conectarse al servidor ssh**

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.081.png)

Vamos a  instalarnos el cliente ssh, para ello:

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.082.png)

Para acceder desde el cliente al servidor tecleamos:

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.083.png)

Nos abríamos conectado remotamente




1. ### **Ejecución remota de aplicaciones gráficas**
Mediante ssh existe la posibilidad de ejecutar aplicaciones gráficas en el servidor y manejarlas y visualizarlas en el cliente. El servidor ssh deberá tener activada la redirección del protocolo X, es decir, deberá tener el siguiente parámetro en el archivo de configuración /etc/ssh/sshd\_config:

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.084.png)

En mi caso ya estaba habilitado , si no lo tuviésemos lo cambiamos y reiniciamos el servicio para que se apliquen los cambios . Ahora deberemos de conectarnos con el parámetro -X :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.085.png)

y posteriormente podemos ejecutar cualquier aplicación gráfica, por ejemplo, gedit:

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.086.png)

Se nos abrirá el programa gráficamente :


![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.087.png)

Ahora vemos en el servidor que se ha creado :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.088.png)

1. ### **Transferir ficheros con ssh**
Para copiar un fichero desde el cliente al servidor introducimos el siguiente comando :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.089.png)

Ahora vamos a comprobar si se ha copiado al servidor :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.090.png)


1. ## **Práctica 2 : Acceso remoto**
   1. ### **Instalación y configuración del acceso remoto**

Vamos a generar nuestras  claves desde nuestro cliente :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.091.png)


Ahora vamos a añadirla a nuestro servidor :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.092.png)

Una vez echo esto deshabilitamos el acceso con contraseña en el servidor editando el archivo /etc/ssh/sshd\_config :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.093.png)

A continuación solo debemos reiniciar el servicio y al volver a registrarnos,  ya estaremos utilizando clave publica :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.094.png)

` `Si nos intentamos registrar con usuario el cual no tenemos la clave publica nos dirá lo siguiente :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.095.png)

**Cambio de puerto**

Ahora vamos a editar el fichero de configuración para indicar el puerto :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.096.png)

Y reiniciaremos el servicio :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.097.png)



Ahora si nos intentamos conectar como lo hemos hecho anterior mente , nos dara el siguiente error :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.098.png)

Para conectarnos deberemos de especificar el puerto por el cual nos conectamos con -p :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.099.png)

### **Conectarnos con un cliente de acceso remoto usando túneles**
Usaremos kitty  , cuando lo abramos en la primera pantalla introducimos la ip del servidor  y el puerto  que haya configurado en el servidor para el ssh en mi caso 2222

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.100.png)







Ahora añadimos el puerto por el cual nos conectaremos usando el túnel y después la ip seguida de dos puntos y el mismo puerto .

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.101.png)



Ahora introducimos nuestro usuario y contraseña y nos habremos conectado :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.102.png)

Si queremos hacer lo mismo pero usando una clave publica desde windows , pulsamos windows +r y escribimos lo siguiente :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.103.png)

Y generamos las claves publicas :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.104.png)

Ahora vamos a la ruta que lo hemos guardado copiamos la clave publica y la introducimos en el servidor , por comodidad la he copiado desde el cliente usando ssh.

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.105.png)

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.106.png)

Una vez añadida guardamos el archivo :

Vamos a desactivar la autenticación por contraseña y reiniciamos el servicio

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.107.png)

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.097.png)

Ahora desde el kitty deberemos de irnos al apartado ssh>auth , le damos a browse y seleccionamos nuestra clave privada , que deberá tener la extension .ppk . Yo la copie en otro   directorio por comodidad para las pruebas .

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.108.png)

Y nos conectamos :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.109.png)

Aquí hemos combinado conectarnos con kitty usando un túnel + otro puerto + clave publica .

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.110.png)


1. ## **Instalación VNCserver**
Lo instalamos con el siguiente comando :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.111.png)

A continuación configuramos las credenciales de configuración para administradores y  usuarios de acceso con el siguiente comando :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.112.png)

Ahora vamos al cliente y introducimos la ip seguida del puerto por  dos puntos, si no lo sabemos lo podemos mirar con  :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.113.png)

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.114.png)

Nos saldrá una advertencia al  no estar cifrada la comunicación , le damos a continuar y  introducimos la contraseña de acceso , que hayamos puesto anteriormente :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.115.png)

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.116.png)

Como no tenemos entrono grafico en el servidor no nos mostrara imagen pero podemos ver que hemos establecido conexión tanto en windows como en Linux  :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.117.png)

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.118.png)

## **Práctica 3: gestión de páginas web mediante ssh**
1.Una vez creado los dos sitio virtuales deseamos establecer una conexión segura a cada uno de nuestros sitios, para ello debemos establecer un túnel ssh de la misma manera que lo hemos establecido para establecer una conexión remota por vnc .

2.Crear un túnel desde el cliente ssh para que el acceso a la sección privada de la web de departamentos se establezca por el puerto 9999

3.Con ambos túneles establecidos comprobar que el acceso a la web iesgn.org se puede realizar sin problemas por el puerto 80

Solo he conseguido hacer a mi pagina por defecto , para eso hacemos un túnel con kitty por ejemplo:

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.119.png)

Ahora añadimos los puertos origen y destino  del puerto :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.120.png)

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.121.png)

Ahora nos registramos con nuestro usuario :

Una vez establecido el túnel introducimos en el navegador localhost:8888 :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.122.png)

Y así hemos establecido una conexión segura web .

Si cerramos el túnel perderemos la conexión :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.123.png)

1. # **APACHE**
1. ## **Práctica 1: Instalar un servidor web Apache para el uso en una Intranet**
Para instalar el servidor debemos ejecutar como root el siguiente comando:

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.125.png)

Crea dentro del directorio /var/www/html un fichero llamado entrada.html en el que pongáis un mensaje de bienvenida

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.126.png)

Ahora  lo meteré dentro de la ruta :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.127.png)

A continuación vamos a publicar una página más completa en nuestro servidor, para ello

utiliza tu sitio web de aplicaciones web.


Ademas debemos de darle permisos de lectura a otros para que podamos visualizarla :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.128.png)

Accede desde los clientes, poniendo en un navegador la siguiente URL:

Desde debian cliente :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.129.png)

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.130.png)

A continuación vamos a publicar una página más completa en nuestro servidor, para ello utiliza tu sitio web de aplicaciones web:

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.131.png)

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.132.png)

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.133.png)

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.134.png)



Resolución local de nombres : modifica los ficheros necesarios en el servicio BIND y accede usando el nombre que has indicado :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.135.png)

Como ya tenia echo el dns anteriormente he utilizado este nombre :

## **Ejercicio 2: Configuración de sitios web virtuales usando Apache**
La primera web tendrá el directorio base será /var/www/iesgn y contendrá una página llamada index.html, donde sólo se verá una bienvenida a la página del instituto Gonzalo Nazareno .

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.136.png)

La segunda web tendrá el directorio base será /var/www/departamentos. En este sitio sólo tendremos una página inicial index.html, dando la bienvenida a la página de los departamentos del instituto.

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.137.png)

Necesitamos tener dos ficheros para realizar la configuración de los dos sitios virtuales, para ello vamos a copiar el fichero 000-default.conf

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.138.png)

Una vez hayamos creado los ficheros añadiremos dentro de cada uno el siguiente contenido :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.139.png)

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.140.png)







Ahora deberemos crear un enlace simbólico en el directorio /etc/apache2/sites-enabled.

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.141.png)

Para que se apliquen estos cambios debemos reiniciar el servicio :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.142.png)

Ahora deberemos de actualizar el dns :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.143.png)

Una vez reiniciado el dns podremos acceder a ambos sitios desde el navegador :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.144.png)

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.145.png)




1. ## **Ejercicio 3: Acceso autentificado al servidor web Apache**
Para activar la autentificación básica debemos de añadir las siguientes lineas a nuestro archivo de configuración del sitio :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.146.png)

Ahora creamos el archivo de las contraseñas , con el usuario previamente creado  :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.147.png)

Reiniciamos el servicio y nos conectamos :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.148.png)

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.149.png)

Ahora vamos ha hacer que a la pagina departamentos solo acceda el director y el profesor , ademas  que a dirección solo acceda el director , para eso añadimos en departamentos:

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.150.png)

Ahora vamos a añadir los usuarios de las zonas para eso , utilizamos este comando :

- Usuario profesor a departamentos :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.151.png)

- Usuario director a departamentos :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.152.png)

- Usuario director a zona dirección :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.153.png)




Ahora reiniciaremos el servicio y comprobaremos que podemos acceder :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.154.png)

Accederemos a departamentos :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.155.png)

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.156.png)

Ahora a la zona equipo directivo :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.157.png)

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.158.png)


# **FTP**
1. ## **Ejercicio 1: Instalación del servidor proFTPd autentificado**
1.Primero nos crearemos un grupo que se llame ftpgroup :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.160.png)

2.Crea dos usuarios locales que pertenezcan al grupo ftp que hemos creado: Jose y Maria

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.161.png)

3.Nos instalamos el servicio ftp :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.162.png)

4.Configuración básica del fichero proftpd.conf:

Todos los usuarios accedan  solo a su directorio :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.163.png)

Ahora podemos acceder desde el navegador con los usuarios jose y maria  :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.164.png)

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.165.png)






Cada uno de estos he creado una carpeta con su nombre dentro de sus directorios personales para poder identificarlos .

Para que cada usuario pueda conectarse realmente al servidor FTP en Debian y le sea posible subir y descargar los datos en su propio directorio, debes introducir su directorio de entrada en proftpd.conf :
1. ## ![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.166.png)
Podemos transferir archivos correctamente :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.167.png)

1. ## **Ejercicio 2: Configuración de proFTPd para crear ftp anónimo**
Lo primero que tenemos que hacer es crear el directorio y darle el propietario adecuado:

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.168.png)

Ahora cambiaremos esta regla y permitiremos que todos puedan unirse :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.169.png)

Ademas añadimos  las siguientes lineas e indicaremos la ruta a la que accederán los anónimos :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.170.png)

Por lo que cuando reiniciemos podrán conectarse los usuarios anónimos :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.171.png)

Pero no con los usuarios que hemos creado anteriormente :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.172.png)

Para permitir que nuestros usuarios se puedan conectar  ademas de los anonimos:

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.173.png)

Ahora aplicamos estos cambios y probamos a conectarnos . Vemos que con anonimos no podemos copiar nada al servidor pero si podemos descargar.

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.174.png)

Ahora con un usuario del grupo , podremos copiar archivos  :

![](/assets/images/serviciosdeb/Aspose.Words.5fca9cc1-3c81-4853-a5ed-a70b0122341b.175.png)
