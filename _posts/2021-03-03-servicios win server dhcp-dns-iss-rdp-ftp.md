---
layout: single
title: Servicios DHCP - DNS - ISS -FTP - RDP -FTP en Windows Server 2019
excerpt: "Practica de servicios en red curso 2021/2022 , en esta se desarolla un escenario con una red local en la que se implantan los servicios NAT ,DNS , DHCP , RDP , SMTP ,POP3 , IMAP ,FTP"
date: 2021-05-22
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

**Esquema de red**

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.001.jpeg)

**Características de las maquinas**

**Maquina Windows server :**

- 2048 MB de ram 
- 32 GB de almacenamiento 
- Tarjeta de red en modo puente y interna 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.002.png)

Las características hardware de la maquina no las he aumentado ya que de momento me parecen suficiente 

**Cliente 1 (Debian ) :**

- 1 GB de ram 
- 10 GB de disco duro 
- Tarjeta de red en modo Red Interna

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.003.png)

He decidido aumentar la ram  para que vaya mas fluido y el almacenamiento por si se necesita en un futuro . 

**Cliente 2 (Windows)** Características : 

- 2GB de ram
- 50 GB de almacenamiento 
- 1 tarjeta de red en modo red interna

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.004.png)

He aumentado las características ya que con las que pide el documento no es posible instalar Windows 10 , he aumentado a 2GB de ram  y a 50 GB de almacenamiento aunque con 1GB de ram y 32 GB de almacenamiento seria suficiente 

Conforme vaya utilizando las maquinas es posible que le aumente la cantidad de núcleos .

**Instalación de las guests additions** 

El software que vamos a instalar  añade funcionalidades a la instalación básica de Virtual Box que mejoran su rendimiento y consiguen un mejor nivel de integración entre la máquina huésped y la máquina anfitriona .

**Maquina Windows server :**

Lo primero que tenemos que hacer es insertar la imagen  con la maquina arrancada , para esto desplegamos  la pestaña dispositivos y al final de esta encontraremos la opción . 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.005.png)

A continuación abrimos el explorador de archivos  nos situamos en este equipo y abrimos el cd .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.006.png)

Una vez abierto seleccionamos el ejecutable de nuestra arquitectura en nuestro caso es el siguiente :

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.007.png)

A continuación se nos abrirá el programa de instalación , pulsamos en siguiente y nos consultara la ruta donde queremos instalarlo en mi caso dejare la por defecto . 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.008.png) 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.009.png)

Ahora seleccionamos todos los programas y le damos a instalar .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.010.png)

Mientras se instala nos saltara una alerta para instalar software de dispositivo deberemos darle a instalar .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.011.png)

Una vez ya acabado el proceso  tendremos que reiniciar , se hará automáticamente si dejamos rebot now seleccionado y pulsamos sobre finish .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.012.png)

**Cliente 1 (Debian ) :**

Para empezar  que tenemos que hacer es insertar la imagen  con la maquina arrancada , para esto desplegamos  la pestaña dispositivos y al final de esta encontraremos la opción . 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.005.png)

A continuación debemos montar el cd , para conocer su ruta podemos hacer un lsblk . En mi caso la ruta del cd es /dev/sr0  y la montare en /media/cdrom como súper usuario .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.013.png)

Ahora nos moveremos a la ruta /media/cdrom y ejecutaremos sudo sh./VboxLinuxAdditions.run

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.014.png)

Para completar la instalación solo debemos reiniciar la maquina 

**Cliente 2 (Windows)**

Para este cliente los pasos son idénticos a los de Windows Server así que pulsa aquí para ir a la explicación .

Una vez instalado nos permitirá cambiar la resolución de nuestra maquina virtual o compartir el portapapeles 

**Nombres de las máquinas** 

Para tener orden voy a llamar las maquinas tal y como están en el esquema del enunciado 

**Maquina Windows server :**

Para cambiarlo en sistemas Windows tal y como indica el enunciado se hace así : Inicio -> Botón derecho en Equipo -> Propiedades -> Cambiar configuración -> Cambiar ... 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.015.png)

**Cliente 1 (Debian ) :**

Para Linux debemos editar el fichero /etc/hostname

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.016.png)

**Cliente 2 (Windows)**

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.017.png)

**Desactivación del Firewall de Windows server**

Para que no tengamos problemas de conectividades vamos a desconectar el cortafuego del Windows Server, para ello :

Inicio -> Herramientas administrativas -> Firewall de Windows con seguridad avanzada -> Y desactivamos los tres perfiles (dominio, privado, público) .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.018.png)

**Configuración de las interfaces de red** 

Voy a seguir el esquema del enunciado :

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.019.png)

**Maquina Windows server :**

En esta maquina disponemos de 2 tarjetas de red :

-Adaptador puente : DHCP

-Red interna: **!**la puerta de enlace sera la ip de la tarjeta adaptador puente

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.020.png)

**Cliente 1 (Debian ) :**

Para configurar nuestra tarjeta de red usamos nano  /etc/network/interfaces , para que se aplique debemos subir y bajar la tarjeta de red con ifup y ifdown .

**!**La puerta de enlace es la dirección ip de la tarjeta de red interna del Windows server 

También he añadido el dns del centro con nano /etc/resolv.conf

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.021.png)

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.022.png)


**Cliente 12 (Windows)**

***!**La puerta de enlace es la dirección ip de la tarjeta de red interna del Windows server* 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.023.png)

**Comprobaciones de conexión** 

**Maquina Windows server :**

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.024.png)

**Cliente 1 (Debian ) :**

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.025.png)


**Cliente 13 (Windows) :** 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.026.png)

Todas las maquinas pueden verse entre si , he realizado con cada maquina un ping a las otras . 

**NAT**

Para ello hay que seguir los siguientes pasos:

1. Inicio -> Herramientas administrativas -> Administrador del servidor -> Agregar roles

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.027.png)

Le damos a siguiente 



2. Seleccionamos la instalación basada en características o roles 
2. Seleccionamos nuestro servidor 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.028.png)

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.029.png)

4. Seleccionamos Acceso remoto y le  damos a  siguiente 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.030.png)



5.En este ventana no es necesaria seleccionar nada , le damos a siguiente 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.031.png)

6.Aquí seleccionamos enrutamiento y le damos a agregar característica 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.032.png)

7.Ahora marcamos la opción de reiniciar automáticamente para automatizar el proceso y le damos a instalar 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.033.png)

8.Ahora volveremos a Administrador del servidor y vamos a  Herramientas> Enrutamiento y acceso remoto  . Seleccionamos nuestro servidor clic derecho  configurar y habilitar .  

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.034.png) 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.035.png)

9.Se nos abrirá un asistente seleccionamos NAT y elegimos la  tarjeta de red con acceso a internet 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.036.png) 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.037.png)

10 . Para terminar seleccionamos configurar mas adelante ya que nosotros no utilizamos DHCP. 

**Comprobación de que ambos clientes navegan**

**Cliente 1 (Debian ) :**

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.038.png)

**Cliente 2 (Windows) :** 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.039.png)

**Servidor DHCP**

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.040.png)

**Instala el rol de servidor DHCP**

En primer lugar tenemos que instalar un nuevo rol en el servidor .Para ello nos dirigimos al administrador del servidor y pulsamos sobre agregar roles y características como hicimos anteriormente  . 

En el tipo de instalación seleccionamos Instalación basada en características o en roles y pulsamos en Siguiente.

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.041.png)

Seleccionamos nuestro servidor  y pulsamos en siguiente para continuar.

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.042.png)

Seleccionamos el rol Servidor DHCP y agregamos las características requeridas que nos indica la ventana emergente que nos aparecerá.

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.043.png) 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.044.png)

En la pantalla de información donde nos explica que es un servidor DHCP pulsamos en Siguiente.

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.045.png)

Confirmamos la selección y le damos a instalar . Yo marcare la opción de reiniciar automáticamente si es necesario para amenizar el proceso 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.046.png)

Deberemos esperar a que se instale 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.047.png)

Una vez finalizado cerramos la ventana y procedemos a realizar la configuración .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.048.png)

**Configuración inicial servidor DHCP**

Para realizar la configuración inicial de nuestro servidor pulsamos en herramientas administrativas → DHCP . Desplegaremos nuestro servidor y seleccionaremos ipv4 una vez hacemos click derecho y ámbito nuevo . 

Se nos abrirá un asistente , le damos a siguiente . Ahora nos pedirá el nombre y una descripción de nuestro ámbito . En mi caso de nombre le pondré iesgn y no pondré descripción 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.049.png) 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.050.png)

Nos pedirán las direcciones ip iniciales y finales  a asignar así como la mascara de subred .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.051.png)

A continuación nos pedirá las exclusiones pero como nosotros no vamos a hacer le damos a siguiente

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.052.png)

Ahora pondremos la duración de la concesión

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.053.png)

A continuación procederemos a configurar la puerta de enlace y dns para ello marcamos configurar ahora .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.054.png)

Para añadir la puerta de enlace la escribimos y le damos a agregar , después a siguiente 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.055.png)

En dominio primario deberemos escribir la dirección de nuestro servidor dns 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.056.png)

Como no vamos a usar servidor wins le damos a siguiente sin escribir nada

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.057.png)

Ahora seleccionamos habilitar este ámbito ahora y finalizamos el asistente de configuración 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.058.png) 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.059.png)

**Cambio de configuración en  los clientes**

**Cliente 1 (Debian ) :**

Deberemos cambiar la configuración de la tarjeta de red de estática a DHCP para ello hacemos nano etc/*network/interfaces*   ademas deberemos reiniciar la tarjeta con ifdown enp0s3 *y ifup enp0s3* 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.060.png)

**Cliente 2 (Windows) :** 

Para ello accedemos Panel de control > redes e internet > conexiones de red > Propiedades de nuestra tarjeta > IPV4 y seleccionamos obtener automáticamente todos los campos . 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.061.png)

**Comprobación de configuración en  los clientes**

**Cliente 1 (Debian ) :**

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.062.png)

**Cliente 2 (Windows) :** 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.063.png)

**Windows server  :** 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.064.png)

**Reserva a un cliente**

Para reservar un dirección ip a un cliente deberemos acceder al conjunto de direcciones seleccionar el cliente que deseemos y darle a agregar a reserva .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.065.png)

Ahora venimos al apartado concesiones y pulsamos sobre la estrella para hacer una reserva nueva , rellenamos el formulario con los datos que deseemos y con la mac del dispositivo . Una vez echo esto le damos a agregar . 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.066.png)

En la carpeta  reserva se nos creara una carpeta con los datos de la reserva que acabamos de crear. Podemos ver si hemos realizado bien la reserva en concesiones de direcciones .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.067.png)

Para que nuestro dispositivo coja la dirección ip que le hemos asignado podemos subir y bajar la tarjeta o esperar a que finalice el tiempo de concesión

**Comprobación de navegación**  

**Cliente 1 (Debian ) :**

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.068.png)

**Cliente 2 (Windows) :**

Podemos ver que la ip de esta maquina es la que le he asignado en la reserva . 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.069.png)

**Parte II**

**Configuración de la red**

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.070.png)

\*la puerta de enlace es mi direcion de la tarjeta de red en adaptador puente . 

**Modifica la configuración del servidor DHCP**

Desactivamos el ámbito nuestro actual y crearemos otro siguiendo el enunciado .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.071.png)

Como la creación de un ámbito esta explicado en un apartado anterior me voy a limitar a indicarte las características de este .

Direcciones ip iniciales e finales  y mascara de subred .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.072.png)

Tiempo de concesión 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.073.png)

Puerta de enlace 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.074.png)

Servidor dns 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.075.png)

Sin servidor wins

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.076.png)

Con esto y reiniciar habríamos acabado de configurar el ámbito.

En nuestros dispositivos clientes en este caso no tendremos que hacer nada solamente reiniciar la tarjeta de red  o reiniciarlos para que se actualice al nuevo ámbito 

**Comprobaciones de concesiones** 

**Cliente 1 (Debian ) :**

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.077.png)

**Cliente 2 (Windows) :**

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.078.png)

**Windows Server:**

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.079.png)

**Reserva parte 2** 

Este apartado esta explicado anteriormente , repetimos el proceso . 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.080.png)

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.081.png)

**Comprobación de navegación**

**Cliente 2 (Windows) :**

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.082.png)

**Servicio dns** 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.083.jpeg)

**Instalación del servicio DNS** 

Para instalar el servicio como en los demás apartados nos  dirigiremos al Administrador del servidor y pulsaremos sobre Agregar roles y características ,. Una vez allí seleccionamos Instalación basada en características o en roles . Seleccionamos nuestro servidor y pulsamos en siguiente , ahora seleccionamos el servicio dns y le damos a agregar características .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.084.png)

En la siguiente ventana no necesitamos seleccionar nada así que le damos a siguiente .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.085.png)En la siguiente ventana le damos a siguiente y seleccionamos instalar , yo he marcado la opción de reiniciar automáticamente para agilizar el proceso .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.086.png)

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.087.png)

Ahora esperamos a que se instale .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.088.png)

Una vez finalizado cerramos el asistente y ya tendremos instalado nuestro servicio dns .

**Configuración del servicio dns** 

Para esto nos iremos a Inicio>Herramientas administrativas de servidor>DNS

Una vez aquí seleccionamos nuestro servidor y podremos ver las distintas tareas que podemos realizar .

**Creación de zonas **

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.089.png)

Las zonas directas son las encargadas de realizar las traducciones de una cadena de nombre de host a la dirección IP.

Las zonas inversas hace lo contrario a las zonas directas, es decir, se encargan de realizar las traducciones de una dirección IP al nombre de host.

Para nuestro servicio vamos a implementar las dos para ello en administrados de dns pulsamos sobre la carpeta zona directa o inversa > nueva zona .

**Creación Zona directa** 

Una vez abierto el asistente  le damos a siguiente  , tendremos que crear una zona ya que nosotros no disponemos de ninguna seleccionaremos la primera opción .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.090.png) 
![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.091.png)

Ahora le pondremos nombre en mi caso iesgn.com

Como no tenemos archivo le damos a crear uno nuevo y a siguiente .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.092.png)

Como nosotros no vamos a utilizar active directory le damos a no permitir actualizaciones .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.093.png)

Le damos a finalizar  .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.094.png)

**Creación Zona inversa**

Nos dirigimos a zona de búsqueda inversa > nueva zona . Se nos abrirá el asistente y le damos a siguiente .**  Seleccionamos crear zona nueva 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.095.png) 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.096.png)

Ahora seleccionaremos zona inversa para ipv4  

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.097.png)

Ahora deberemos introducir el nombre de la zona inversa introduciendo la dirección ip de nuestra red o el nombre directamente . En la siguiente ventana le daremos a crear archivo puesto que no tenemos uno previo .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.098.png) 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.099.png) 

Al igual que en la zona directa no permitiremos las actualizaciones dinámicas puesto que no usamos active directory 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.100.png)

Ahora le damos a finalizar 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.101.png)

**Creación de los FQHN**

Para ello nos dirigimos a  nuestra zona de búsqueda directa y le damos a añadir host nuevo (A o AAAA)

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.102.png)

Ahora introducimos el nombre doraemon y añadimos la ip 192.168.1.1

Nos indicara que se ha creado  correctamente

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.103.png)

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.104.png)

Ahora deberemos de repetir esto para crear todos los FQHD y nos debería quedar así :

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.105.png)

**Servidor de correo** 

Al igual que en el apartado anterior nos dirigimos  a  nuestra zona de búsqueda directa y le damos a añadir host nuevo (MX) . Y rellenamos el formulario .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.106.png)

Ahora deberemos crear un host  A como en el apartado anterior 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.107.png)

Posteriormente hacemos doble clic sobre nuestro host mx y seleccionamos a nuestro host A 

Ahora estarán enlazados correctamente 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.108.png)

**Servidor FTP** 

Repetimos los pasos anteriores solo que ahora seleccionamos la opción (CNAME) le pondremos ftp y la enlazaremos con dorami 

**Búsqueda inversa **


![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.109.png)

Nos vamos a la zona inversa > clic derecho >nuevo puntero PTR 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.110.jpeg)

Ahora le damos a examinar , nos dirigimos a nuestro ámbito y seleccionamos cada uno de los FQDN . Y se nos rellenaran los demás campos automáticamente  , le damos a siguiente y continuamos  haciendo esto hasta tenerlos todos creados .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.111.png)

**Modificación DHCP** 

Para que el servidor DHCP le de a nuestros clientes el dns deberemos de ir a nuestro ámbito y opciones de ámbito , servicio dns y poner la dirección de nuestro servidor dns  . 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.112.jpeg)

**Configuración de los clientes** 

En mi caso no tendré que tocar nada manualmente de configuración ya que todo se asigna automáticamente . Lo único que hay que hacer es reiniciar los equipos una vez echo el apartado anterior para que se actualice el dns o subir y bajar las tarjetas de los clientes 

**Comprobaciones** 

Doraemon.iesgn.com

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.113.png)

iesgn.com y www.iesgn.com (captura echa después de realizar servicio web)

ftp.iesgn.com

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.114.png)

nobita.iesgn.com

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.115.png)

El servidor de correo configurado para iesgn.com

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.116.png)

La  dirección ip de www.josedomingo.org 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.117.png)

El nombre de la dierecion 192.168.0.203 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.118.png)

El servidor dns que tiene configurado iesgn.com 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.119.png)

**Navegación en cliente Windows** 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.120.jpeg)

**Navegación en cliente debian** 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.121.png)

**Configuración de los clientes** Windows cliente 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.122.png)

Debian cliente 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.123.png)

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.124.png)

**Configurar  reenviadores**

En  nuestro administrador de dns , accedemos a renviadores condicionales , acemos clic derecho y seleccionamos nuevo reenviador condicional 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.125.png)

Tendremos la siguiente ventana la cual deberemos rellenar 

En domino dns deberemos poner el nombre con el que se guardara el grupo de renviadores , en la tabla del centro pondré las direcciones ip de los servidores dns de google .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.126.png)

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.127.png)

Una vez echo esto le daremos a actualizar y ya tendríamos los reenviadores configurados 

**Servicio Web (IIS)**

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.128.jpeg)

**Instalación del servicio ISS**

Con el servicio nat se me instalo parcialmente parte del servicio web , para evitar posibles problemas mas adelante he buscado una guia y según esta he añadido las características que no tenia instaladas . [Aquí](https://help.mproerp.com/help/0000000059/) te lo dejo .

Al igual que en los servicios anteriores accedemos a agregar roles y características 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.129.jpeg)

Seleccionamos nuestro servidor 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.130.jpeg)Ahora deberemos tener seleccionado servidor web  y dentro de estos asegurarnos de que tenemos instaladas todas las siguientes características . 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.131.png)

También deberemos de instalar todas las características del menú desarrollo de aplicaciones . Cuando las seleccionaremos deberemos aceptar agregar las características . 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.132.png)

Ademas de lo anterior también debemos agregar las siguientes características 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.133.png)

En la siguiente pestaña de añadir características no deberemos de añadir nada . Avanzamos y le damos a instalar . 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.134.png)

Una vez haya finalizado podremos cerrar el asistente . 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.135.png)

**Ejercicio1: Instalar un servidor web IIS para el uso en una**

**Ejercicio 1.1** 

En la ruta c:/inetpub/wwwroot he creado el archivo  entrada.html el cual contiene :

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.136.png) 
![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.137.png)

Desde el navegador de Windows server buscamos http://localhost/entrada.html y nos muestra lo siguiente :

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.138.png)

Y para acceder desde los clientes deberemos introducir la puerta de enlace seguido de /entrada.html

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.139.png)

**Ejercicio 1.2** 

Accedemos a Administrador de Internet Information Services (IIS) y cremos nuestro sitio 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.140.png)

Si introducimos  http://localhost vemos mi proyecto correctamente desde el servidor 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.141.jpeg)

Y para verlo desde el cliente introducimos la puerta de enlace 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.142.jpeg)

**Ejercicio 1.3** 

Para ello modificamos ambos ficheros host tanto como el del cliente como el del servidor y nos quedaría tal que así .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.143.jpeg)Una vez guardados podremos acceder usando una url , sin usar el dns . Aquí en el cliente 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.144.png)

Y aquí accedemos desde el servidor 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.145.png)

**Ejercicio2: Configuración de sitios web virtuales usando IIS**

Primero creare el sitio web IES para realizar el ejercicio.

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.146.jpeg)

Después creare el sitio web  departamentos 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.147.png)

Previamente he creado las carpetas y las rutas . Aquí te las muestro .Primero la carpeta IES

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.148.png)

Y aquí la carpeta departamentos 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.149.png)

Ahora modificaremos los ficheros host de los clientes y del servidor . Todos devén quedar como este para visualizar ambas paginas 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.150.png)

Una vez modificado podremos visualizar ambas paginas .Aquí la comprobación del servidor :

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.151.png)

Y aquí la comprobación desde el cliente 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.152.png)


![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.153.png)

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.154.png)

**Ejercicio 3: Acceso autentificado al servidor IIS** 

Anteriormente ya me instale el servicio al rol de IIS 8: Autentificación básica .Así que lo primero que deberemos hacer sera habilitar la autenticación básica y deshabilitar la anónima .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.155.png)

En el directorio base de (c:inetpub/ies ) vamos a crear una carpeta llamada “profesores”, que será la carpeta que vamos a controlar su acceso por medio de la autenticación

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.156.png)

Dentro de esta carpeta crea un archivo index.html con un mensaje de bienvenida a la zona privada de los profesores.

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.157.png)

Vamos a crear una serie de usuario y un grupo llamado “Profesores”, vamos a crear cuatro usuarios: Alicia, Luisa, Jesús y Raúl . Para crear los usuarios Inicio->Herramientas administrativas- >Administración de equipos-> Usuarios y grupos locales . Una vez hay clic derecho y crear usuario . Tendremos que rellenar este formulario simplemente poniendo nombre de usuario y contraseña . También desmarcaremos la primera casilla para no tener que cambiar la contraseña .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.158.png) 
![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.159.png)

Una vez creados vamos a crear  un grupo llamado Profesores, y vamos añadir a este grupo sólo los usuarios Alicia y Luisa. Para esto pinchamos sobre la carpeta grupos y clic derecho nuevo grupo .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.160.png)

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.161.png)

A continuación, le damos los permisos necesarios a la carpeta C:/inetpub/ies/profesores, para ello ir al botón derecho→Editar permisos→seguridad . Desde aquí deshabilitamos la herencia desde opciones avanzadas . Y hacemos lo siguiente , quitar el grupo Usuarios, para no permitir el acceso a ningún usuario.

-Agregar el grupo Profesores, con los permisos con los permisos de “Lectura y ejecución”, “Mostrar el contenido de la carpeta” y “Leer”, de modo que cuando la ventana de la imagen superior presente el aspecto mostrado en la imagen inferior, pulsaremos sobre el botón “Aceptar”.

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.162.png)

Ahora vamos a comprobar si podemos acceder a <http://www.iesgn.com/profesores> desde el cliente con los diferentes usuarios  .Nos pedirá el nombre de usuario y contraseña .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.163.png)

Primero accederé con Alicia que pertenece al grupo profesores 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.164.png)

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.165.png)

Ahora intentare acceder con raul que no pertenece a al grupo profesores .g

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.166.png)

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.167.png)

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.168.png)

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.169.png)

Como vemos no nos deja conectarnos ya que no pertenecemos al grupo profesores . 

**Ejercicio 4 : Configurar el DNS para que haga la resolución de nombres del sitio Web creado.** 

Para hacer la resolución dinámica debemos de ir a administrador de dns . Una vez aquí deberemos de crear un alias nuevo (CNAME) .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.170.png)

Debemos de tener en cuenta que nuestra pagina este en nuestra zona . 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.171.png)

En el nombre del alias deberemos introducir el nombre de nuestra pagina podemos verlo desde IIS, debemos de asegurarnos que el FQDN coincidan , si nos fijamos en el primer apartado solo introduzco www ya que es lo que falta . 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.172.png)

Y en el ultimo apartado elegimos el host , en mi caso doraemon que tiene la ip 192.168.0.1  que creamos previamente.

Una vez echo esto pulsamos sobre actualizar archivos de datos del servidor .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.173.png)

Ahora deberemos ir a los clientes y comentar las lineas del fichero host .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.174.png)

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.175.png)

Ahora comprobaremos si funciona en los clientes y nos funcionara .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.176.png)

También podemos comprobarlo con nslookup

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.177.png)

**Servicio remoto** 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.178.jpeg)

**Instalación del servicio** 

Al igual  que los servicio anteriores accedemos a administración del servidor > Agregar roles y características 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.179.png)

Nos saltamos las pestañas ya que no vamos a modificar nada . En la pestañas de servicios de rol seleccionaremos todas las opciones menos host de virtualización . Yo no he podido instalar la característica de acceso web debido a un error pero como no la vamos a utilizar no es relevante .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.180.png)Ahora tenemos que comprobar que hemos añadido las características y le damos a instalar . Y marcamos la casilla de reiniciar automáticamente .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.181.jpeg)

Esperamos a que finalice .

**Configuración del acceso remoto en el servidor**

Deberemos de permitir en nuestro servidor el acceso remoto , accediendo a propiedades del sistema , acceso remoto y permitir conexiones remotas . 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.182.png)

**Acceder desde el cliente al servidor remotamente**

Ahora para conectarnos a este equipo nos vamos al cliente y podemos iniciar el programa de control remoto buscando por conexión a escritorio remoto .

También podemos acceder a esta aplicación pulsando la tecla Windows + R y escribiendo mstsc.exe
![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.183.png)

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.184.png)

Una vez abierto el programa debemos de introducir el nombre de nuestro equipo o direccion de red 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.185.png)

Ahora deberemos de introducir las credenciales de nuestro usuario administrador .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.186.png)

Es posible que si no tenemos los certificados configurados nos salte este aviso , pero como estamos seguros del equipo que vamos a controlar le damos a si . 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.187.png)

Como podemos ver se nos ha conectado 

Ahora me conectare usando su dirección de red .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.188.png)

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.189.png)

Como no he introducido ningún usuario nos lo preguntara así como sus credenciales .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.190.png)

Como vemos ahora en vez de mostrarnos el nombre del equipo nos dirá su dirección de red .

**Crea un usuario con permisos de acceso remoto y conectate**

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.191.png)

Accedemos a usuarios y grupos locales y añadimos el nuevo usuario como hicimos en el servicio anterior . 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.192.png)

Ahora pulsamos sobre el usuario para darle permisos 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.193.png)

Debemos irnos a propiedades del usuario y darle permisos de control remoto 

Ademas debemos de añadir en propiedades del sistema a nuestro usuario creado 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.194.png)

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.195.png)

Ahora nos iremos al cliente y accederemos con el usuario que acabamos de crear . Ponemos nuestra dirección de red y nuestro usuario .

Ahora introducimos nuestra contraseña 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.196.png)

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.197.png)

Como ves hemos accedido al servidor con el usuario que acabamos de crear .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.198.png)

**Software gratuitos de acceso remoto** 

Algunos ejemplos de estos software son : 

**-AnyDesk:** programa completamente gratuito para uso personal que nos permite conectarnos a un ordenador de forma remota desde cualquier parte del mundo. Ademas esta aplicación es multiplataforma y se encuentra disponible en Windows, macOS, iOS, Android, Linux, Chrome OS y Raspberry Pi. También nos permite el envió de archivos de forma remota asi como conexiones seguras y fiables . 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.199.png)

**-SupRemo:** es gratuita y de uso personal ademas es multiplataforma pero esta disponibles en menos sistemas que AnyDesk estando  solo  disponible  en Windows,  macOS, iOS, Android . En comparación con estos , este permite tener varias conexiones simultáneamente .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.200.png)

-TeamViewer: Este es muy conocido y esta muy extendido  nos permite conectarnos remotamente ademas es usado en entornos profesionales . Este nos permite grabar las sesiones y un sistema de chat .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.201.png)

**Instalación de TeamViewer**

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.202.png)

Vamos a su pagina web  y nos dirigimos a Windows aquí te dejo el [enlace](https://www.teamviewer.com/es/descarga/windows/). Pulsamos en descargar la versión de 64 bits que son nuestros sistemas .

Esperamos a que se descargue el instalador y lo abrimos .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.203.png)

Instalamos con los ajustes predeterminados y le damos a siguiente .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.204.png)

Nos pedirá permisos de administrador y se los debemos de dar para que se instale .Ahora esperamos que se instale .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.205.png)

Cuando acabe se nos abrira una pestaña para aceptar el acuerdo de licencia , marcamos la casilla y confirmamos 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.206.png)

**Usar TeamViewer para controlar un equipo remotamente** 

Cuando abrimos el programa nos mostrara los datos que debemos darle a la persona para que se conecte remotamente 

Conociendo estos datos desde el servidor introducimos los datos del cliente
![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.207.png)

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.208.png) 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.209.png)

Como vemos estamos controlando el equipo con este programa para salirnos de la conexión podemos pulsar la x y finalizara .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.210.png)Cuando finalizamos las sesiones como tenemos una versión gratuita nos saltara este aviso pero podremos seguir usándola

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.211.png)

**Accede desde tu servidor windows al servidor de un compañero de clase**

Para ello debemos estar conectado a la misma red . Deberemos introducir la direcion ip de la tarjeta externa del compañero a conectarnos en mi caso Juan Diego .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.212.png)

A continuación introducimos el usuario y las credenciales de su usuario del servidor , el introducio las de su usuario administrador .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.213.png)

Como ves me he conectado a su servidor 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.214.png)

**Servidor FTP**

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.215.png)

**Instalación del servicio ftp** 

Para instalar el servicio accedemos a administración del servidor > agregar roles y características > tipo de instalación seleccionamos basada en roles y seleccionamos servidor ftp , que estara al desplegar servidor web . 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.216.png)

En los siguientes apartados no sera necesario seleccionar nada . En confirmar selección marcamos la casilla de reiniciar y comenzamos la instalación . 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.217.png)

Una vez finalice la instalación podremos cerrar el asistente 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.218.png)

**Configuración del servicio**

Para configurar nuestro sitio ftp primero deberemos de crear una ruta donde almacenemos nuestros archivos en mi caso sera c:/inetpub/ftp/public . Dentro de esto crearemos los archivos que se compartirán .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.219.png)Una vez echo esto nos dirigimos al IIS y hacemos clic derecho sobre nuestro server , aquí seleccionamos agregar sitio ftp . 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.220.png)

Se nos abrirá un asistente en el cual deberemos de ponerle un nombre al sitio y indicar la ruta que hemos creado anteriormente

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.221.png)Ponemos en dirección ip ponemos nuestra puerta de enlace ya que lo mantendremos localmente en nuestra red . Permitimos el SSL y seleccionamos nuestro certificado .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.222.png)

Seleccionamos autenticación anónima y permitimos el acceso a usuarios anónimos . Ademas le damos permisos de lectura . 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.223.png)

Accedemos a nuestra pagina ftp desde el iis y nos metemos en reglas de autorización . 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.224.png)

Una vez dentro crearemos comprobamos que se haya creado correctamente la regla anterior .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.225.png)

Si no se ha añadido , agregaremos a todos los usuarios anónimos y le daremos permisos de lectura .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.226.png)

A continuación , para hacer que podamos encontrar nuestro servicio con un nombre utilizaremos el dns , accedemos a el y crearemos un cname y lo vincularemos a doraemon .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.227.png)

Nuestra zona dns debería quedar así : 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.228.png)

**Comprobación desde los clientes** 

Para acceder a través de la ip introducimos en el navegador [ftp://192.168.0.1](ftp://192.168.0.1/)

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.229.png)

Si queremos acceder usando un nombre deberemos de poner [ftp://ftp.iesgn.com](ftp://ftp.iesgn.com/)

**Configuración de un servidor FTP con acceso autentificado** 

Lo primero que haremos sera crear el sitio ftp . Le asignamos el nombre que queramos y seleccionamos de ruta [c:\users](file:///c:/users)

Repetimos la configuración del ejercicio anterior , ponemos la ip 192.168.0.1 y permitimos el certificado ssl .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.230.png)

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.231.png)

En esta ventana  seleccionamos usuarios anónimos con permisos de lectura y le damos a finalizar .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.232.png)

Crearemos los usuarios Jose y maría  accediendo a usuarios y grupos locales .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.233.png)

Comprobaremos que se han creado correctamente

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.234.png)

Una  vez  echo  esto  deberemos  de  crearle  sus  directorios  correspondientes  a c:/usuarios/LocalUser/Jose   c:/usuarios/LocalUser/Maria  y  le  meteré  algún  archivo  para visualizarlo.

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.235.png)

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.236.png)

Ahora comprobaremos que puedo acceder como Jose y maría . Primero con Jose

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.237.png)

Como vemos puedo acceder como Jose 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.238.png)

Ahora lo haremos con maría 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.239.png)

Vemos su directorio 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.240.png)

Como vemos accedemos directamente al directorio del usuario .

**!!Para que cada usuario entre en directamente en su directorio he realizado lo siguiente :** En aislamiento habilitamos la tercera opción 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.241.png)

Ahora nos dirigimos a nuestras carpetas de los usuarios y le damos permiso solo a ese usuario . A Jose : 

Y a maría :
![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.242.png)

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.243.png)

Ademas debemos de tener habilitada la autenticación básica y deshabilitada la anónima 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.244.png)

**Mi solución al error** 

5)Para que puedan acceder usuarios anónimos debemos habilitar la autentificación anónima y en la reglas de autorización debemos añadir la opción de usuarios anónimos. Los usuarios anónimos accederán a una carpeta llamada: c:/usuarios/LocalUser/Public 

**!!He estado investigando y al tener habilitada el aislamiento de usuarios no es compatible con la autenticación anónima , en el articulo que he encontrado habla de active directory pero creo que es aplicable a nuestro caso ya que el error es el mismo . Te dejo el enlace [aquí](https://docs.microsoft.com/es-es/troubleshoot/iis/error-530-anonymous-ftp-sites) .** 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.245.png)

**Así , que una posible solución que he encontrado es crear un usuario local en el servidor  que tenga el nombre de anonymous y crear su directorio al igual que hicimos con Jose y maría ya que estos van ligados a los usuarios .** 

**Tengo entendido que al usar este sistema de aislamiento los directorios van ligados a los nombres de usuarios ,  por lo que acceder a la carpeta public con el usuario que acabamos de crear no seria posible .**

**Si podríamos tener acceso , usando aislamiento , si tenemos un usuario que se llame  public .** Te enseño lo que he echo , creo su directorio :

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.246.png)

Creo el usuario :

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.247.png)

Le damos permiso al usuario .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.248.png)

Metemos a anonnymous el usuario que acabamos de crear 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.249.png)

Como ves podemos acceder al directorio .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.250.png)

Claro, esto es un usuario local como Jose y Maria , por eso funciona .

**Acceder con usuario anónimo y subir archivos** 

Lo primero es darle permisos de escritura al usuario en la carpeta localmente .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.251.png)

Ahora nos iremos al explorador de archivos y buscaremos ftp://192.168.0.1

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.252.png)Para añadir un archivo podemos arrastrarlo por ejemplo , como ves se ha añadido a la carpeta . También podríamos copiarlo y pegarlo 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.253.png)

Estos se guardaran el la ruta donde acceda nuestro usuario en este caso aquí .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.254.png)

**Gestión de páginas web mediante acceso FTP**

Vamos a crear dos sitios webs virtuales en el servidor IIS que se llamen web1.iesgn.com y web2.iesgn.com . 

Primero creare sus directorios :

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.255.png)

Ahora creare las dos web , primero web1

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.256.png)

y web2

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.257.png)

Ahora crearemos los usuarios web1 y web2 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.258.png)

Ahora modificaremos el servidor dns para que haga la resolución de nombres parra ello crearemos los correspondientes registros cname . 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.259.png)

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.260.png)

Nuestro dns quedaría así : 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.261.png)

Ahora nos conectaremos a través de ftp y subiremos los archivos de las paginas web comprimidos .

Pero antes de esto deberemos darle permisos de escritura y lectura a los usuarios web a sus respectivos directorios .

Primero a web1

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.262.png)

Por ultimo a web2

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.263.png)

Ahora nos dirigimos al cliente y nos conectamos con los dos usuarios a traves de ftp en el explorador de archivos . 

Primero con el usuario web1

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.264.png)

Ahora pasamos la carpeta comprimida a nuestro ftp .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.265.png)

Repetimos lo mismo con el usuario web2

Y pasamos la carpeta comprimida 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.266.png)

Ahora deberíamos de acceder a las paginas web pero si accemos esto nos saldrá esto :

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.267.png)

Para solucionar esto deberemos ir a IIS y cambiar el documento predeterminado .

En mi caso los index se llaman web1.html y web2.html asi que los añadiremos y una vez echo esto deberemos de descomprimir la carpeta para que lea los archivos . 

De modo que el directorio quedaría así para web1 :

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.268.png)

y así para web2

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.269.png)

Así quedaría el documento predeterminado de web1

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.270.png)

Y así quedaría el documento predeterminado de web2

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.271.png)

Ahora te mostrare el resultado desde los clientes . Desde windows10 se vería así web1

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.272.png)

Desde windows10 se vería así web2

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.273.png)

Desde debian se vería así web1
![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.274.png)

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.275.png)

Desde debian se vería así web2

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.276.png)

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.277.png)

**Instalación y configuración de un servidor/cliente FTP gratuito**

5 Servidores ftp populares :

**-Cyberduck :** Un cliente FTP Mac muy interesante para los usuarios del sistema operativo Mac OS. La principal funcionalidad que ofrece es que se puede integrar con los editores de códigos más relevantes y utilizados del mercado. Además, hace las funciones de cliente para Google Docs y Amazon S3.

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.278.png)

**-WinSCP:** Un cliente SFTP que hace uso de la tecnología Secure Shell para garantizar la máxima seguridad a los usuarios. Permite la transferencia de datos y archivos entre ordenadores locales y remotos de forma completamente segura, sin fisuras. Se trata de un cliente FTP Windows, disponible sólo para este sistema operativo.

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.279.png)

**-Transmit:** Un cliente FTP de pago para Mac OS y otros dispositivos con sistema operativo iOS. Una de las grandes ventajas que ofrece es que la transmisión de datos se realiza de manera muy rápida. Además, gracias a la función de sincronización los usuarios tienen plena libertad para ajustar directorios completos para su transmisión con el servidor. No hay que olvidar que admite la encriptación SSL y SSH, lo cual es un gran punto a favor en términos de seguridad.

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.280.png)

**-SmartFTP:**Un software compartido compatible con Windows que admite los protocolos FTP, FTPS y SFTP. Una de sus funcionalidades más destacadas es que establece plazo para las transferencias y, además, reanuda aquellas transferencias que se han interrumpido por cualquier motivo. Tiene capacidad para conectarse de manera simultánea a varios servidores.

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.281.png)

**-FileZilla:** Casi con total seguridad, uno de los mejores clientes FTP en la actualidad. Ofrece soporte para FTP sobre SSL / TLS (FTPS) y SSH File Transfer Protocol (SFTP). También una gran selección de funciones, como por ejemplo el sistema de configuración en red o la transferencia en cola. Se trata de un cliente gratuito y, además, disponible para Windows, Mac OS y Linux.

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.282.png)

**Instalación de FileZilla**

Lo primero que deberemos de hacer es descargarlo en nuestro servidor para ello buscamos en nuestro navegador la pagina oficial de FileZilla , aquí te dejo el [enlace](https://filezilla-project.org/).

Deberemos seleccionar la opción de server .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.283.png)

Pulsaremos sobre donwload FileZilla server .

Nos saldrá el siguiente aviso deberemos agregar la pagina para que podamos descargar al archivo si no el navegador no confiara y no permitirá la descarga .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.284.png)

Nos saldrá este aviso en la parte inferior del navegador le daremos a guardar para que se descargue 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.285.png)

Cunado finalice la descarga le daremos  ejecutar 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.286.png)

Ahora comenzara el proceso de instalacion , lo primero que tenemos que hacer es aceptar la licencia de uso .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.287.png)

Aquí dejamos marcadas todas las opciones y le damos a next

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.288.png)

Ahora seleccionamos la ruta donde se instalara , yo dejare la predeterminada 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.289.png)

Ahora deberemos elegir los accesos directos . Yo dejare los que vienen asi que le damos a next

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.290.png)

Ahora deberemos elegir varias opciones , la primera es cuando queremos que se inicie , la segunda el puerto por el cual escuchara la administración de la interfaz y las contraseñas de administracion que le pondremos 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.291.png)

Ahora elegiremos cuando se iniciaría la interfaz de administración 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.292.png)

Y le damos a instalar y esperamos que finalice 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.293.png)

Se  nos abrirá automáticamente una ventana de administración como esta :

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.294.png)

Ahora rellenamos esta ventana con los siguientes datos :

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.295.png)

Ahora deberemos guardar la firma

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.296.png)

Nos saldrá la siguiente ventana pulsamos sobre server > configure

Ahora nos movemos a usuarios , le damos a adduser y le ponemos el nombre que queramos , yo al crear el usuario que no necesita autentificación es decir el anónimo lo he llamado anonnymous . 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.297.png)

Le dejamos la opción que no requiere contraseña y le ponemos la ruta de la carpeta public por ejemplo. Y marcamos la opción de writeable para poder escribir . 

Ahora creare la zona autenticada , para esto repetimos , crearemos un usuario yo le pondré Jose , le damos que requiera contraseña y le indicamos la ruta de la carpeta Jose . Y marcamos la opción de writeable

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.298.png)

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.297.png)

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.299.jpeg)

**Instalación del cliente** 

Accedemos a su pagina web igual que con el servidor y seleccionamos la opción de cliente 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.300.png)

Pulsamos sobre descargar 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.301.png)

Y seleccionamos la primera opción

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.302.png)

Le damos a ejecutar 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.303.png)

Le damos permisos pulsando en si

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.304.png)

Aceptamos el acuerdo de licencia 

Denegamos el programa adicional

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.305.png)

Ahora nos preguntara si lo queremos instalar para este usuario o para todos , en mi caso seleccionare solo para mi . 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.306.png)

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.307.png)

Dejamos seleccionadas las predeterminadas

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.308.png)

Introducimos la ruta donde se instalara , en mi caso dejare la predeterminada 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.309.png)

Ahora se crearan los accesos directos , lo dejaremos como viene 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.310.png)

Y cuando finalice la instalación le damos a finish .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.311.png)

Una vez finalizado se nos abrirá el programa , si tenemos el FileZilla apagado podemos usar el ftp de la actividad 2 y3 podremos acceder como  poniendo  la dirección ip y los datos de los usuarios, nos saldrá una ventana como esta ya que el certificado es desconocido así que le damos a aceptar y nos conectara a la carpeta del usuario .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.312.png)

Ahora vamos a conectarnos a FileZilla server así que detenemos todos los sitios ftp.

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.313.png)

Ahora introducimos en el cliente la dirección ip del servidor y el usuario anonymous , como vemos sin introducir contraseña hemos podido acceder anónimamente , abajo a la derecha podemos ver el contenido de la carpeta 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.314.png)

Ahora probaremos a subir un archivos desde FileZilla para esto seleccionamos el archivo y le damos a subir 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.315.png)

Podremos asegurarnos de que se ha transferido en la parte inferior en transferencias satisfactorias .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.316.png)

Vamos a hacer lo mismo con el usuario Jose el cual nos tendremos que identificar 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.317.png)

Transferiré el archivo y veremos que se ha transferido satisfactoriamente . 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.318.png)



Ahora descargaremos los dos archivos que hemos subido , primero con Jose el usuario autenticado pulsamos sobre el archivo y le damos a descargar  

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.319.png)

Aquí podemos ver que se ha descargado 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.320.png)

Ahora con anonnymous descargare el archivo publico 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.321.png)

Aquí la transferencia satisfactoria vemos que se ha realizado . 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.322.png)

**Servidor de correo**

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.323.png)

**Instalación**

Al igual que en los servicios anteriores debemos ir a administración del servidor > agregar roles y características . Una vez aquí nos vamos a características y seleccionamos servidor smtp .

Cuando pulsamos sobre esta nos pedirá agregar características , le damos a agregar 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.324.png)

Una vez marcada la opción le damos a siguiente 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.325.png)

Marcamos la opción de reiniciar si fuese necesario y le damos a instalar 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.326.png)

Una vez instalada podemos cerrar el asistente 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.327.png)

Ahora nos descargaremos el servidor de correo hMailServer , aquí te dejo el [enlace](https://www.hmailserver.com/download) .

Deberemos añadirle a sitios de confianza para que nos permita descargar el archivo.

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.328.png)

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.329.png)

Guardamos el archivos

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.330.png)

Cuando finalice la descarga le damos a ejecutar . 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.331.png)

Se nos abrirá el asistente , le damos a siguiente 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.332.png)

Aceptamos el acuerdo de licencia y le damos a siguiente 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.333.png)

Ahora seleccionamos la ruta , yo dejare la predeterminada 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.334.png)

Seleccionamos las opciones que queramos instalar , yo las dejaras todas . 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.335.png)

Ahora elegimos el tipo de base de datos 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.336.png)

Ahora seleccionamos el nombre del acceso directo , yo dejare el que viene 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.337.png)

Ahora deberemos de crear una contraseña de administración 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.338.png)

Ahora  nos mostrara un resumen de lo seleccionado , si vemos que es correcto le damos a instalar

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.339.png)

Una vez finalizado , marcamos la casilla y le damos a finish para que se inicie al cerrar .

Ahora nos conectamos al servidor dándole a conect

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.340.png)

Ahora introducimos nuestra contraseña

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.341.png)

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.342.png)

Se nos abrirá una ventana como esta , ahora le damos a add domain y le ponemos iesgn.com

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.343.png)

Una vez echo esto le damos a save .

Ahora vamos a poner que use el protocolo POP3 , nos vamos a settings > protocols .Y solo dejamos esta seleccionada

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.344.png)

**Añadir usuarios** 

Nos vamos debajo de nuestro dominio y en accounts le damos a add .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.345.png)

Ahora rellenamos el formulario en mi caso solo le he puesto dirección y lo he guardado 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.346.png)

Lo mismo con el usuario2 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.347.png)

**Añadir entradas al dns**

Vamos a nuestra zona y creamos un nuevo registro mx uno para smtp 

Y otro para pop3 ![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.348.png)

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.349.png)

Así quedaría nuestro dns 

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.350.png)

**Utiliza  Thunderbird para acceder al servidor de correo instalado**

Abrimos Thunderbird y añadimos las 2 cuentas , en hostname deberemos poner la ip del servidor .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.351.png)

Cuando le demos a done nos saldrá este aviso , le damos a entiendo el riesgo y le das a confirmar .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.352.jpeg)

Ahora con el usuario1 le mandare un correo al usuario2

Miraremos la bandeja de entrada del usuario2 , nos ha llegado correctamente .

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.353.png)

![](/assets/images/servicioswinserver/Aspose.Words.a00cdc9b-6cbd-4eb4-8a5a-1066339caa45.354.png)

