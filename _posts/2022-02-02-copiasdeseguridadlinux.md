---
layout: single
title: ¿Como hacer copias de seguridad en Linux?
excerpt: "Practica de seguridad informática curso 2021/2022 , en esta se desarolla un entorno para comprobar la eficacia de los distintos sistemas de copias de seguridad "
date: 2022-02-02
classes: wide
header:
  teaser: /assets/images/prueba/logo.png
  teaser_home_page: true
  icon: /assets/images/logo.jpg
categories:
  - Seguridad
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

**Copias incrementales**

Crea una carpeta llamada datos con tres ficheros con distintos contenidos:

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.001.png)

Dentro de cada fichero le he puesto el nombre del mismo . 

**Primer día**

Realiza una copia completa de esa carpeta con el comando tar (los ficheros lo vamos a ir numerando como si las copias la hiciéramos en distintos días, es decir el fichero resultante se llamaría copiacompleta1ddmmyyyy.tgz, donde ddmmyyyy es la fecha de la copia).

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.002.png)

**Segundo día** 

Modifica el fichero1.txt, borra el fichero2.txt y crea un nuevo fichero fichero4.txt. Realiza una copia incremental del directorio 

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.003.png)

Ahora haré la copia de incremental del directorio :

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.004.png)

**Tercer día** 

Modifica el fichero3.txt y crea un nuevo fichero fichero5.txt. realiza un copia incremental del directorio 

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.005.png)

Y la copia incremental quedaría así : 

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.006.png)

**Cuarto día**

Crea un directorio carpeta1 y dentro crea un nuevo fichero fichero6.txt. Realiza una copia incremental del directorio 

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.007.png)

**Quinto día** 

Borra el fichero1.txt y renombre la carpeta a carpeta2. Realiza una copia incremental del directorio 

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.008.png)

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.009.png)

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.010.png)

**Sexto día** 

Realiza otra copia completa del directorio 

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.011.png)

**Séptimo día** 

Crea otro directorio carpeta3 y dentro el fichero fichero7.txt. Borra el fichero4.txt. Realiza una copia incremental del directorio 

El fichero 6 ya esta en la  carpeta2 , así que en la carpeta3 he creado el fichero 7 .

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.012.png)

**Octavo día** 

Borra el fichero5.txt. Realiza una copia incremental del directorio

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.013.png)

**Restauración**

Para ello deberemos de restaurar la completa y después la incremental . Yo lo haré sobre un directoria llamado datos .

**Octavo día:**

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.014.png)**

**Quinto día:**

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.015.png)

**Tercer día:**

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.016.png)

**Copias diferencial**

Vamos a repetir el mismo ejercicio pero ahora las copias serán así : 

- Primer día: Copia completa
- Segundo día: Copia diferencial
- Tercer día: Copia diferencial
- Cuarto día: Copia diferencial
- Quinto día: Copia diferencial
- Sexto día: Copia completa
- Séptimo día:Copia diferencial
- Octavo día:Copia diferencial

Repetimos la misma estructura que el ejercicio anterior :

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.017.png)

**Primer día** 

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.018.png)

**Segundo día**

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.019.png)

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.020.png)


**Tercer día**

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.021.png)

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.022.png)

**Cuarto día**

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.023.png)

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.024.png)

**Quinto día**

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.025.png)

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.026.png)

**Sexto día**

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.027.png)

**Séptimo día**

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.028.png)

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.029.png)



**Octavo día**

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.030.png)

**Restauración Octavo día**

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.031.png)

**Quinto día**

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.032.png)


**Tercer día**

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.033.png)

**¿Ocupan más las copias diferenciales o las copias incrementales?**

Ocupan mas las diferenciales que las incrementales ya que  copia todos los datos nuevos o modificados desde la última copia completa.

**Copias mixtas**

Vamos a repetir el ejercicio, realizando las mismas modificaciones a los ficheros, pero realizando las siguientes copias:

- Primer día: Copia completa
- Segundo día: Copia incremental
- Tercer día: Copia incremental
- Cuarto día: Copia diferencial
- Quinto día: Copia incremental
- Sexto día: Copia incremental
- Séptimo día: Copia diferencial
- Octavo día: Copia incremental

**Primer día**

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.034.png)

**Segundo día**

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.035.png)

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.036.png)



**Tercer día**

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.037.png)

**Cuarto día**

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.038.png)

**Quinto día**

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.039.png)

**Sexto día**

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.040.png)

**Séptimo día**

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.041.png)

**Octavo día**

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.042.png)



**Restauración Octavo día** 

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.043.png)

**Quinto día** 

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.044.png)

**Tercer día** 

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.045.png)

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.046.png)

**Automatización de copias de seguridad utilizando cron**

**Ejercicio 1** 

Busca información para crear 3 scripts en bash para crear una copia completa, incremental y diferencial de la carpeta datos. Los nombres de los ficheros generados deben contener la fecha.

**Copia completa :**

#!/bin/bash

DATE=$(date +%Y-%m-%d-%H%M%S) BACKUP\_DIR="/home/javiercruces/copias/" SOURCE="/home/javiercruces/datos/"

tar -cvzpf $BACKUP\_DIR/backup-$DATE.tar.gz $SOURCE

**Copia incremental :**

#!/bin/bash BACKUP\_DIR="/home/javiercruces/copias/" ROTATE\_DIR="/ carpetadestino /backup/rotate" TIMESTAMP="timestamp.dat" SOURCE="/home/javiercruces/datos/" DATE=$(date +%Y-%m-%d-%H%M%S)

EXCLUDE="--exclude=/mnt/\* --exclude=/proc/\* --exclude=/sys/\* --exclude=/tmp/\*" cd /

mkdir -p ${BACKUP\_DIR}

set -- ${BACKUP\_DIR}/backup-??.tar.gz lastname=${!#} backupnr=${lastname##\*backup-} backupnr=${backupnr%%.\*} backupnr=${backupnr//\?/0} backupnr=$[10#${backupnr}]

if [ "$[backupnr++]" -ge 30 ]; then

mkdir -p ${ROTATE\_DIR}/${DATE}

mv ${BACKUP\_DIR}/b\* ${ROTATE\_DIR}/${DATE} mv ${BACKUP\_DIR}/t\* ${ROTATE\_DIR}/${DATE} backupnr=1

fi

backupnr=0${backupnr} backupnr=${backupnr: -2} filename=backup-${backupnr}.tar.gz

tar -cpzf ${BACKUP\_DIR}/${filename} -g ${BACKUP\_DIR}/${TIMESTAMP} -X $EXCLUDE ${SOURCE]

**Copia diferencial :**

#!/bin/bash

echo introduce la fecha de la ultima copia 

read fecha

tar -cpvzf "copiadiferencial\_`date +%d%m%Y`.tar" datos/ -N $fecha

Deberemos de darle permisos de ejecución a los scrpits con chmod +x nombredescript 

**Ejercicio 2**

Explica el funcionamiento de cron y documenta cómo lo utilizaríamos para automatizar el proceso de copia de seguridad según el siguiente esquema:

Cron es un administrador de tareas de Linux que permite ejecutar comandos en un momento determinado, por ejemplo, cada minuto, día, semana o mes. Si queremos trabajar con cron, podemos hacerlo a través del comando crontab.

Para configurar nuestras copias elegiremos la primera opción:

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.047.png)

Ahora ponemos las siguientes lineas , deberemos poner primero cuando queremos que se ejecute el scrpit y después la ruta de donde se encuentra . 

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.048.png)

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.049.png)

**Copias de seguridad en Linux con programas de terceros**

Me descargare el programa Gadmin-Rsync desde el centro de software ya que he visto que me permite programar copias y ademas seleccionar el tipo de la misma cosa que otros programas no me permitían .

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.050.png)

La primera vez que lo lancemos nos pedirá la contraseña de root:

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.051.png)

Ahora creamos una copia completa 

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.052.png)

Nos preguntara donde queremos guardarla , le daremos a copia local :

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.053.png)

Seleccionamos el directorio que queremos hacerle las copias 

Ahora seleccionamos donde se guardaran las mismas 

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.054.png)

Vamos a hacer una copia completa manualmente para eso pulsamos sobre nuestra configuración  y al botón de run selected backup 

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.055.png)

Tenemos un apartado para ver el progreso del mismo :

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.056.png)

Ahora vamos a programar las horas y las copias para automatizarlas :

Antes de esto deberemos de crear la copia diferencial y incremental como hemos creado antes la completa  . Ahora seleccionamos arriba la copia nos desplazamos abajo y seleccionamos las horas y días que se realizaran 

La programación de la diferencial :

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.057.png)![](Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.058.png)

Y por ultimo la copia incremental :

![](/assets/images/seguridad/copiasseguridadlinux/Aspose.Words.a5ea697f-26fc-496e-b5ca-3341b4f207fa.059.png)

Este software da muchas ventajas a personas que no tienen conocimientos sobre el tema ya que el programa es muy intuitivo . Sin embargo la clara desventaja es que al ser dedicado al gran publico perdemos muchas opciones de personalización que nos permite un scrpit por ejemplo .

