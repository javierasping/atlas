---
layout: single
title: Instalacion y configuracion Active Directory en Ubuntu Server 20.04 LTS
excerpt: "Proyecto final SOR , instalacion de active directory bajo Ubuntu y administracion remota del servidor "
date: 2022-06-01
classes: wide
header:
  teaser: /assets/images/prueba/logo.png
  teaser_home_page: true
  icon: /assets/images/logo.jpg
categories:
  - Sistemas
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


**Introducción**

Se quiere configurar un servidor Linux (Ubuntu Server 20.04 LTS) para dar servicio a un conjunto de equipos clientes (Windows y Linux).

Aprovecharé que el escenario lo tenemos montado de las anteriores actividades de clase y restauraré  las  instantáneas para disponer de las máquinas limpias .

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.001.png)

**Preparación entornó**

\1. El servidor Linux no tendrá entorno gráfico. Tendrá al menos las particiones: raiz, home y de intercambio.

Aquí podemos ver que no tengo instalado entorno gráfico , podemos ver que el servicio está activo, sin embargo, no se lanza ningún entorno . Además, si buscamos algún proceso con los nombres de escritorio más conocidos no nos lanza ningún resultado .

Aquí te muestro  las particiones  que tiene mi servidor Ubuntu  (raíz , boot , home y swap):

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.002.png)

2.El servidor debe estar preparado para que pueda administrarse de forma remota (a partir de este momento toda la gestión se hará remotamente desde otro equipo de la red).

Para administrarlo de forma remota utilizaré ssh, para ello lo instalamos en el servidor :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.003.png)

Una vez que se instale lo tendremos funcionando , no es necesario realizar ninguna configuración .

Si consultamos el estado del servicio podemos ver que ha tomado la configuración por defecto :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.004.png)

Para conectarnos remotamente necesitaremos saber la IP del equipo o el nombre :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.005.jpeg)

En mi caso me conectaré desde la red externa a nuestro servidor (enp0s3) , previamente hemos configurado la red con netplan :

Y hemos aplicado los cambios :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.006.png)

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.007.png)

Una vez conociendo estos datos nos conectaremos por ssh desde una máquina de nuestra red para seguir con los demás apartados, en mi caso utilizaré mi máquina host, para ello me he instalado el paquete openssh-client previamente:

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.008.jpeg)

3. Crea los usuarios y grupos siguientes:
- Grupos: profesores, alumnos, smr, asir. Creo los grupos :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.009.png)

- Usuario a crear :  profedesiree, profejose , proferaul , erik, manu, oliver, sandra, fabio y domi

Creo los usuarios :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.010.png)

Los he creado con directorio home y les he asignado la contraseña 1234 (son de ejemplo) .

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.011.png)


- Usuarios del grupo profesores: profedesiree, profejose y proferaul. Los añadimos :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.012.png)

Podemos comprobar que se han añadido con el siguiente comando :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.013.png)

- Usuarios del grupo alumnos: erik, manu, oliver, sandra, fabio y domi. Los añadimos :

Comprobamos que se han añadido :
![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.014.png)

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.015.jpeg)

- Usuarios del grupo smr: profedesiree, profejose, proferaul, erik, manu y oliver.

Los añadimos:

Comprobamos que se han añadido :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.016.png)

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.017.png)

- Usuarios del grupo asir: sandra, fabio y domi.

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.018.png)

Comprobamos que se han añadido :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.019.png)

4. Todos los usuarios serán usuarios Samba. Para ello deberemos tener instalado samba :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.020.png)

Para añadir un usuario samba debemos de introducir el siguiente comando y asignarle una contraseña :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.021.png)

Esto lo haremos con los 9 usuarios , una vez añadidos podemos utilizar este comando para listar los usuarios samba que tenemos :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.022.png)

**Controlador de dominio samba**

5. Crea y configura un controlador de dominio Samba en el Servidor.

Antes de comenzar con la instalación debemos de tener en cuenta una serie de datos :

-Nombre del controlador de dominio de *Active Directory*: FJCD

-Nombre DNS del dominio de *Active Directory*: javiercruces*.local*

-Nombre del Reino Kerberos: javiercruces.local

-Nombre NetBIOS del dominio: javiercruces

-Dirección IP fija del servidor: 192.168.0.1

-Rol del servidor: Domain Controller (DC)

-Reenviador DNS:192.168.0.1

Una vez con estos datos claros comenzaremos con la instalación , lo primero será actualizar el sistema :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.023.png)

A continuación deberemos de cambiar el nombre de nuestro servidor para estar acorde con los datos que hemos seleccionado anteriormente, para ello yo he seleccionado mis iniciales , para ello editamos el fichero */etc/hostname* :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.024.png)

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.025.png)

Ahora será necesario que reiniciemos el equipo para que se apliquen los cambios , perderemos la conexión por ssh :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.026.png)

Retomamos el control remoto por ssh en unos minutos cuando haya reiniciado :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.027.png)

Como puedes observar nos hemos conectado usando el antiguo nombre que tenia nuestro servidor , esto es porque el archivo /etc/hosts, contiene una relación de direcciones IP con sus correspondientes nombres lógicos. Este archivo contenía una referencia al nombre antiguo del propio servidor, que cambiaremos para que haga referencia al nuevo nombre :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.028.png)

Una vez hemos aplicado estos dos cambios , antes de continuar solo nos quedara asegurarnos de que nuestro servidor tiene correctamente configurada la red . En nuestro escenario disponemos de dos tarjetas de red en nuestro servidor :

enp0s3 (Tarjeta externa , nos da acceso a internet)

enp0s8 (Tarjeta interna , es la que se comunica con nuestra red local)

Debido a esto la primera está configurada por DHCP, ya que no nos importa la configuración que se le asigne , sin embargo, la segunda está configurada estáticamente, ya que debemos de controlar la configuración de la misma para que tengamos control sobre la misma y posteriormente unir los equipos al dominio .

Una vez aclarado esto , al principio del documento indico como se configuraran las interfaces , aquí dejo un pantallazo para recordar las direcciones :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.029.jpeg)

Ahora necesitaremos disponer de unos paquetes que deberán de estar instalados antes de comenzar . Estos son :

samba: servidor de archivos, impresión y autenticación para SMB/CIFS. smbclient: clientes de línea de comandos para SMB/CIFS.

krb5-config: Archivos de configuración para Kerberos Version 5.

winbind: Servicio para resolver información sobre usuarios y grupos de servidores Windows NT.

Podremos hacer la instalación de estos cuatro paquetes con un simple comando :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.030.png)

Kerberos, nos preguntará por el reino (nombre de dominio ) durante la instalacion de los paquetes, en nuestro caso será javiercruces.local :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.031.jpeg)

Aquí introduciremos el nombre de nuestro equipo servidor :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.032.png)

Aquí volveremos a introducir el nombre de nuestro servidor :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.033.png)

Después de esto, la instalación continuará un poco más, pero sin necesitar que aportemos más información:

Ahora configuraremos samba , pero antes de hacerlo le cambiaremos el nombre al archivo de configuración *smb.conf* para que no lo use mientras que lo configuramos y así además tendremos una copia del archivo original :


![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.034.jpeg) 

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.035.png)

Usaremos el comando samba-tool domain provision, para que sea el propio comando sea el que nos solicite los valores que necesite y, cuando sea posible, nos sugiera sus valores predeterminados. Así, si estos coinciden con los que nosotros esperamos, será muy probable que los pasos anteriores hayan sido los correctos:

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.036.png)

Como puedes observar es muy intuitivo hacerlo, ya que salvo la IP de forwarder y la contraseña de administrador hemos elegido las respuestas que el mismo comando nos ofrece . Esta  debe cumplir unos requisitos de complejidad mínimos :

-8 caracteres como mínimo

-1 mayúscula

-1 numero

Con esto, además de configurarse Samba , se ha generado un archivo de configuración para Kerberos en la ruta /var/lib/samba/private/krb5.conf. Asi que lo copiaremos a /etc :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.037.png)

Lo siguiente será configurar la resolución de nombres, para ello comenzaremos deteniendo los servicios implicados :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.038.png)

También quitaremos que se inicien automáticamente al reiniciar el equipo :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.039.jpeg)

A continuación, nos aseguraremos de que el servicio samba-ad-dc se podrá iniciar sin dificultades, evitando cualquier enmascaramiento que pueda existir:

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.040.png)

Después, eliminamos el archivo resolv.conf que, en realidad, será un enlace a stub-resolv.conf. Así que lo eliminamos y creamos uno nuevo para sustiruirlo:

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.041.png)

Ahora introducimos los valores adecuados en función de nuestro dominio , para mi caso :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.042.png)

Guardamos los cambios y salimos del fichero.

Iniciaremos el servicio de samba-ad-dc y lo habilitaremos para que se inicie al reiniciar el equipo :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.043.png)

**Comprobar la instalación**

Si hemos conseguido llegar hasta aquí , tenemos todas las papeletas para que nuestra instalación haya sido correcta . Pero nunca está de más hacer unas comprobaciones

**Consultar el nivel del dominio y crear un nuevo usuario**

Para saber nuestro nivel de dominio simplemente introducimos este comando :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.044.png)

Al hacerlo, comprobamos que el nivel del dominio, y del bosque donde se encuentra, equivale a una instalación Windows Server 2008 R2

Probaremos a crear una nueva cuenta de usuario en el dominio con el comando(deberemos de tener en cuenta la política de contraseñas):

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.045.png)

**Confirmar que el servidor DNS funciona de forma adecuada**

Lo primero será comprobar el servicio LDAP sobre el protocolo TCP, para lo que escribiremos la siguiente orden:

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.046.png)

Si tenemos una respuesta parecida a esa, todo funciona como debe.

A continuación, comprobaremos el registro SRV para el protocolo Kerberos sobre UDP, para lo que usamos la siguiente orden:

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.047.png)

La respuesta debe ser parecida a la anterior, si es así  registro SRV es correcto.

Por último, comprobamos la resolución del nombre de nuestro servidor:

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.048.jpeg)

**Comprobar el funcionamiento de Kerberos**

Para comprobar el funcionamiento  podemos, por ejemplo, usar el comando smbclient para comprobar los servicios que puede obtener un determinado usuario. Para ello utilizaremos el siguiente comando :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.049.png)

Si la autenticación es correcta , ya sabremos que Kerberos está haciendo su trabajo . Si queremos, incluso podemos iniciar sesión en el servidor empleando la cuenta de administrador. Para lograrlo, usaremos una sintaxis como esta:

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.050.png)

Ya hemos verificado todo así que podemos empezar a unir clientes a nuestro dominio .

**Unir clientes al dominio**

6. Integra al menos un cliente con Windows en el dominio Samba. **Cliente Windows**

Lo primero que haremos será configurar la red de nuestro cliente :

-IP 192.168.0.10

-Mascará de subred /24

-Puerta de enlace 192.168.0.1

-DNS 192.168.0.1

\*Ambas tarjetas (Interna del servidor y la de Windows cliente ) deberán de estar en red interna para que se comuniquen .

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.051.png)

Una vez configurada la tarjeta le haremos un ping al servidor para comprobar la conectividad:

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.052.png)

Ahora accedemos a panel de control → sistema y seguridad → sistema → configuración avanzada del sistema → nombre de equipo → id de red . Seleccionamos la primera opción para unirnos al dominio

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.053.png)

Seleccionaremos la primera opción, ya que nuestra red tiene un dominio :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.054.png)

Ahora deberemos de introducir los datos del usuario administrador y el nombre de nuestro dominio :

\*El usuario administrador que se crea por defecto en samba se llama administrator

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.055.png)Una vez introducido los datos nos preguntará si queremos crear una cuenta de dominio en este equipo , yo seleccionare que no :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.056.png)

Y para que se apliquen los cambios deberemos de reiniciar :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.057.png)

Una vez reiniciado podremos iniciar sesión con los diferentes usuarios de nuestro dominio : 

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.058.jpeg)

Podemos ver que podemos iniciar sesión en el equipo con las cuentas de nuestro dominio:

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.059.jpeg)

**Cliente Linux**

Lo primero será configurar la red, para ello le he asignado la dirección IP 192.168.0.2

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.060.jpeg)

Ahora deberemos añadir a nuestro servidor en el fichero hosts, una línea en la que ira la dirección IP de nuestro servidor seguido del nombre de este y el nombre completo del dominio de nuestro servidor  :

Para comprobar este cambio que hemos realizado le haremos un ping al servidor usando su nombre :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.061.jpeg)

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.062.jpeg)

Ahora actualizaremos el equipo para poder descargar las versiones más recientes desde los repositorios :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.063.png)

\*Para tener internet en el cliente he configurado previamente NAT en el servidor .

Una vez actualizado el sistema instalaremos los siguientes paquetes :

- sssd (System Security Services Daemon): Administra los mecanismos de autenticación y el acceso a directorios remotos. Sustituye al clásico Winbind aportando más velocidad y estabilidad.
- heimdal-clients: Se trata de una implementación libre de Kerberos 5 creada con la intención de ser compatible con el protocolo Kerberos implementado por el MIT.
- msktutil: La utilidad que obtiene y administra los keytabs de Kerberos en un entorno de Microsoft Active Directory.

Podemos hacerlo con 1 comando :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.064.png)

Mientras instalamos nos solicitara el nombre de nuestro servidor de active directory asi que lo introducimos :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.065.png)

Ahora nos preguntará el nombre del equipo que actúa como servidor  en nuestro caso es :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.066.png)

Por  último nos preguntará por el servidor administrativo que en nuestro caso es el mismo:

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.067.png)

Una vez hecho esto, la instalación continuará sin que tengamos que introducir más datos.

Ahora vamos a añadir en Kerberos unos datos adicionales para asegurarnos que se comporte correctamente. Comenzaremos por cambiar el nombre del archivo de configuración, para poder volver a los parámetros originales si fuese preciso:

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.068.png)

Ahora utilizaremos nano para editar la configuración del archivo , este estará vacío así que añadiremos lo siguiente :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.069.jpeg)

Una vez rellenado con los datos de nuestro dominio, guardamos el archivos y comprobaremos si podemos iniciarnos sesión en el dominio :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.070.png)

Si la salida no nos ofrece ningún tipo de error, es porque el proceso de autenticación ha funcionado correctamente.

Procederemos a unirnos al dominio, para ello utilizaremos el siguiente comando :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.071.png)

Este comando deberemos de rellenarlo conforme a los datos de nuestro dominio , en el caso de que no nos salga ninguna salida , nos habremos unido al dominio .

Para completar la tarea, eliminaremos los tickets de autorización de kerberos que activamos al ejecutar kinit. Para lograrlo, basta con utilizar el comando kdestroy.

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.072.png)

**Compartir carpetas**

7. Se necesitan carpetas personales en el servidor para cada usuario. También habrá una carpeta para cada grupo, a la que solo podrán acceder y escribir los miembros de cada grupo.

Vamos a crear los directorios en la partición raíz para cada usuario y uno para cada grupo. Estos los crearé con el nombre del grupo o usuario:

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.073.png)

\*Tenemos que tener en cuenta que los usuarios samba que hemos generado al principio del documento se han eliminado al instalar el dominio y deberemos de producirlos nuevamente.

Vamos a compartir estas carpetas a través de samba, para ello editamos el fichero /etc/samba/smb.conf :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.074.jpeg)

Para indicar que pueda acceder un grupo deberemos de poner una @ delante dele nombre del grupo :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.075.jpeg)Solo nos quedaría asignar correctamente los permisos locales adecuados para nuestros recursos y cambiar los propietarios de las carpetas para que los usuarios puedan escribir en ellas :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.076.png)

Esto sería lo correcto, pero si le asignamos los permisos 775 no podremos escribir en la carpeta, así que le asignaremos todos los permisos :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.077.png)

Ahora repetiremos esto con todos los directorios , primero le daré los permisos:

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.078.png)

Y por último cambiaremos los propietarios de las carpetas y haremos a cada usuario o grupo sus respectivos dueños :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.079.png)

Vamos a asegurarnos de que hemos aplicado correctamente estos cambios :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.080.png)

Vamos a comprobar que podemos acceder a los recursos compartidos desde el usuario oliver  :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.081.jpeg)

Vamos a acceder  a la carpeta Oliver y a crear un directorio dentro :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.082.png)

8. Desde Windows acceder a estas carpetas a través de unidades de red.

Desde el explorador de archivos podremos ver todos los recursos compartidos en la red :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.081.jpeg)

Ahora vamos a crear unidades de red, así que por ejemplo vamos a añadir la carpeta Oliver al usuario Oliver como unidad de red, para esto , hacemos clic derecho en la carpeta > conectar a unidad de red :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.083.png)

Y seleccionaremos una letra para asignarle a la unidad de red  :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.084.jpeg)

Ahora esta unidad nos aparecerá en este equipo :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.085.jpeg)

**Perfiles móviles**

9. Definir perfiles móviles en el servidor Linux mediante Samba, de forma que los usuarios se puedan autentificar en diferentes máquinas Windows, manteniendo su configuración. Para realizar esto vamos a instalarlos RSAT (Remote Server Administration Tools) que nos permitirá administrar nuestro controlador de dominio samba de forma idéntica a windows server .

Para añadirlas buscaremos en la búsqueda de Windows ***Añadir características opcionales ,*** una vez aquí le daremos a añadir característica :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.086.png)

Una vez aquí buscaremos las siguientes características con RSAT y las instalaremos  :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.087.png)

Una vez instaladas se nos creará una aplicación similar a la de un Windows server llamada herramientas administrativas :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.088.png)

Se nos abrirá una carpeta con las herramientas de administración :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.089.jpeg)

Y buscaremos administración de usuarios y equipos de active directory o escribimos en ejecutar dsa.msc , esto lo haremos con el usuario administrador de nuestro dominio para poder acceder a esta:

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.090.png)Antes de crear nuestro usuario móvil crearemos un recurso de red al igual que hemos hecho anteriormente llamado perfiles y le daremos permisos al grupo móviles para que estos puedan escribir en ellos :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.091.png)

Para que nuestro usuario pueda escribir en este directorio lo añadiremos al grupo :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.092.png)

Ahora nos vamos a la configuración de nuestro usuario y le cambiamos la ruta del perfil . Pondremos la ruta de nuestra carpeta compartida perfiles seguida de ***\%username%*** :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.093.png)

Guardamos y ya tendríamos hecho nuestro perfil móvil creado .

Vamos a demostrar el funcionamiento del perfil móvil , para ello le he cambiado el fondo y he creado dos carpetas  :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.094.jpeg)

Ahora vamos a cerrar sesión e iniciarla en el Windows de la derecha :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.095.jpeg)

Vemos que se ha realizado correctamente el perfil móvil .

**NFS**

10. Mediante NFS, se compartirán en el servidor las carpetas: proyectos, documentación, programas\_y\_drivers. De la primera solo se podrá leer; en las dos últimas también se podrá escribir. Los equipos Linux montarán las carpetas automáticamente en el arranque.

Lo primero que haremos será instalarnos los siguientes paquetes :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.096.png)

Ahora crearemos en la raíz los directorios que vamos a compartir :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.097.png)

Y le cambiaremos el propietario y los permisos a estos directorios :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.098.png)

Después de esto, debemos editar el archivo /etc/exports. Este es el archivo donde se indican a NFS las carpetas que vamos a compartir . La primera será solo de lectura y las dos últimas se podrán escribir :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.099.png)

Para poder acceder a estos recursos en el servidor vamos a instalarlos los siguientes paquetes :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.100.png)

Ahora vamos a crear los directorios donde montaremos nuestras carpetas :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.101.png)

Para montarlas manualmente en Linux haremos el siguiente comando  :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.102.png)

Vamos a comprobar que en proyectos no podremos escribir :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.103.png)

Mientras que en las otras dos si podremos escribir :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.104.png)

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.105.png)

Si queremos acceder a estos recursos en Windows : - \\192.168.0.1\documentacion

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.106.png)

-\\192.168.0.1\proyectos (directorio de solo lectura)

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.107.png)

-\\192.168.0.1\programas\_y\_drivers

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.108.png)

Para poder visualizarlos será necesario tener instalados las siguientes características en Windows (Podemos acceder a este programa a través del buscador de Windows escribiendo características de Windows)

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.109.png)

Para finalizar con este punto vamos a configurar que los equipos Linux monten automáticamente al arrancar los directorios . Editaremos el fichero /etc/fstab añadiendo las siguientes líneas :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.110.png)

Una vez hecho esto reiniciamos y veremos que se nos habrán montado automáticamente:

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.111.png)

**Cuotas**

11. La carpeta /home del servidor tendrá un sistema de cuotas para evitar la saturación con archivos de los usuarios (100 MB por usuario).

Lo primero que haremos será instalar los paquetes para implementar cuotas :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.112.png)

Ahora permitiremos las cuotas en la particion /home añadiendo esto al fstab de nuestro servidor :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.113.png)

Remontamos la partición home para que se apliquen estos cambios :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.114.png)

Y aplicamos cuotas en la partición /home

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.115.png)

Comprobaremos que en la raíz de la partición se nos ha creado dos archivos (aquota.group y aquota.user):

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.116.png)

Ahora le aplicaremos la cuota de 100Mb a oliver  usando edquota :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.117.png)

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.118.png)

Ahora usaremos una herramienta la cual es *gawk,* el cual nos permitirá concatenándolo con este comando, aplicarle la cuota que le acabamos de crear a Oliver a todos nuestros usuarios :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.119.png)

La orden que acabamos de lanzar ha extraído una lista de todos los usuarios y ha aplicado la cuota de Oliver a todos usuarios con un UID mayor a 499 .

Ahora revisaremos las cuotas para ver como han quedado :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.120.jpeg)

Para comprobar que funciona vamos a agotar la cuota del usuario proferaul , para ello crearemos un archivo de 30 MB :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.121.png)

Ahora lo moveremos al directorio home de él y le haremos propietario del archivo :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.122.png)

Vemos que se actualiza el espacio usado en el directorio del usuario :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.123.png)

**Webmin**

12. Instala Webmin en el servidor para tener la posibilidad de gestionarlo gráficamente desde un cliente. Demuestra alguna de sus funcionalidades.

Webmin es un panel de control web moderno que le permite administrar su servidor Linux a través de una interfaz basada en navegador.

Necesitaremos instalar apache para poder instalar webmin en nuestro servidor :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.124.png)

Ahora deberemos de añadir el repositorio de webmin , así que editaremos el sources.list y lo añadiremos :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.125.png)

Guardamos el archivo y haremos un apt update para actualizar los repositorios , nos saldrá un error advirtiéndonos de que el repositorio no es fiable :![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.126.png)

Así que ahora descargaremos la clave PGP de Webmin y la añadiremos a nuestro sistema :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.127.png)

Volvemos a hacer un apt update y veremos que ahora el repositorio es fiable

A continuación descargaremos el paquete webmin :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.128.png)

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.129.png)

Las últimas líneas de la instalación nos dará los datos para acceder vía web a este servicio :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.130.png)

Así que en un cliente vamos al navegador y accedemos a esta url :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.131.jpeg)Nos dirá que la conexión no es privada , para saltarnos esta advertencia Configuración avanzada > acceder

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.132.png)

Tendremos un portal donde deberemos entrar con un usuario administrador de nuestro servidor :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.133.png)

Lo primero que veremos en la interfaz web será un monitor de recursos, así como datos de nuestro equipo :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.134.jpeg)

Podremos ver un histórico del monitor de recursos, el cual nos mostrara las horas y el porcentaje de uso de nuestro hardware, así como información del sistema :

Tenemos más apartados como el de logins recientes o interfaces de red , el cual nos dará información de quien se ha conectado y las configuraciones de las mismas respectivamente :


![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.135.jpeg) 

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.136.jpeg)

Para finalizar con el panel tendremos una última ventana la cual nos dirá el uso del disco y particiones :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.137.png)

Una vez que hemos echado un vistazo a la página principal vamos a aprovechar una funcionalidad que tiene que nos permite ver los directorios compartidos por nfs , para acceder aquí vamos a networking > NFS exports :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.138.jpeg)

Vamos, que además nos permite editar los directorios compartidos actuales, así como añadir o eliminar estos .

Además, esta herramienta nos permite configurar un Firewall con iptables , lo cual hoy día es de vital importancia disponer de seguridad en nuestra red :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.139.jpeg)

Incluso dispone de una terminal web para que podamos administrar el servidor desde un cliente , para acceder a esta desplegamos el menú y pulsamos sobre el símbolo de terminal o pulsamos Alt + K :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.140.png)

Vemos que usara ssh con el usuario conectado en la aplicación , en mi caso javiercruces :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.141.png)

Webmin incluye muchas más funciones de administración que nos ayuda a trabajar con el servidor de forma gráfica para hacer más ameno la administración del mismo ,desde actualizar paquetes hasta configurar un Firewall . Además, usa https, por lo que nuestro tráfico viajara cifrado , lo que nos permitiría configurar nat para poder acceder desde un dispositivo que este fuera de nuestra red , sin que un snifer pueda descifrar nuestro trafico fácilmente. Es aconsejable que cambiemos el certificado auto-firmado que usa webmin por uno propio que podemos generar con Let`s encrypt, por ejemplo .

**CUPS**

13. Habrá un servidor de impresión CUPS, que se administrará desde un cliente Ubuntu. Lo primero que deberemos de hacer es instalar en el servidor cups :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.142.png)

Una vez hecho esto vamos a configurar el servicio para permitir ser administrado desde nuestro cliente Ubuntu , para ello editamos el siguiente fichero :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.143.png)

Ahora añadiremos los siguientes parámetros :

Listen 192.168.0.1:631

allow 192.168.0.0/24

Para permitir que nuestro cliente Ubuntu sea capaz de administrar el servicio

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.144.png)

Ahora solo nos quedaría reiniciar el servicio :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.145.png)

Nos desplazaremos al cliente y en el navegador introduciremos la ip de nuestro servidor seguido de dos puntos y 631 :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.146.jpeg)

Con esto hemos comprobado que el cliente puede administrar cups .

14. Configura una impresora en red para todos los usuarios, con límites de páginas diarias para todos los usuarios.

Para compartir nuestra impresora en red , accedemos al panel web y en el apartado de administración marcamos compartir impresoras conectadas a este sistema :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.147.jpeg)

Antes de establecer los límites vamos a habilitar que el servicio registre el nombre de los usuarios al mandar archivos , para ello en el fichero cupsd.conf cambiamos este valor de default a none :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.148.png)

Ahora reiniciaremos el servicio :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.145.png)

Para establecer un límite diario para cada usuarios de 20 páginas por ejemplo , aplicaríamos el siguiente comando para nuestra impresora .

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.149.png)

Una vez aplicado este comando los usuarios solo podrán imprimir el número indicado de páginas ,cuando supere el límite los trabajos se mandaran a cups , pero este los desechara de la cola y no los imprimirá :

![](/assets/images/sistemas/proyecto_ad_ubuntu/Aspose.Words.582694fc-b92b-4748-a44e-690fed1b5e3f.150.jpeg)

Es decir, el trabajo 21 en este ejemplo no se creará hasta qué pasen 24 horas .


**Bibliografía**

[Como saber que escritorio tengo ](https://www.sysadmit.com/2020/06/linux-como-saber-que-escritorio-tengo.html)[Montar controlador de dominio samba ](http://somebooks.es/crear-un-controlador-de-dominio-de-active-directory-con-samba-en-ubuntu-18-04-lts/)[Configurar la red con netplan](http://somebooks.es/establecer-una-direccion-ip-estatica-ubuntu-server-17-10-posteriores/)

[Unir cliente linux a dominio parte 1 ](http://somebooks.es/unir-un-cliente-ubuntu-20-04-a-un-dominio-de-active-directory-sobre-windows-server-2019-parte-1/)[Unir cliente linux a dominio parte 2 ](http://somebooks.es/unir-un-cliente-ubuntu-20-04-a-un-dominio-de-active-directory-sobre-windows-server-2019-parte-2/)[Administrar dominio con RSAT ](http://somebooks.es/12-7-administrar-el-controlador-de-dominio-resara-con-rsat/)[Acceder carpetas compartidas w10 ](http://somebooks.es/nfs-parte-6-acceder-a-la-carpeta-compartida-desde-un-cliente-windows-10/)[Cuotas](https://www.linuxtotal.com.mx/index.php?cont=info_admon_018)

[Instalación y uso de webmin ](https://www.digitalocean.com/community/tutorials/how-to-install-webmin-on-ubuntu-20-04-es)[Comandos CUPS](https://docs.oracle.com/cd/E26921_01/html/E25809/gllgm.html)

