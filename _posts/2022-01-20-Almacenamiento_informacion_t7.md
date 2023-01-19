---
layout: single
title: ¿Como utilizar particiones en linux y windows ?
excerpt: "Practica de seguridad informatica  2021/2022 , en esta se desarolla el particionado de discos para utilizarlo en sistemas Linux y Windows "
date: 2022-01-10
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

**En la maquina Windows** 

**1.Crea un disco virtual de 100MB y agrégalo a la MV.**

Para esto nos dirigimos a nuestra maquina virtual le damos a configuración > almacenamiento > añadir disco virtual 

Le damos a crear 

![](/assets/images/seguridad/almacenamiento_informacion_t7/Aspose.Words.f91a77a0-a719-41c5-af36-35e0757f51ed.001.png)

Seleccionamos el tipo de disco que queremos en mi caso vdi la primera opción 

![](/assets/images/seguridad/almacenamiento_informacion_t7/Aspose.Words.f91a77a0-a719-41c5-af36-35e0757f51ed.002.png)

Nos preguntaran a continuación como tratara nuestro sistema anfitrión el espacio del nuevo disco , en  mi caso seleccionare diatónicamente .

![](/assets/images/seguridad/almacenamiento_informacion_t7/Aspose.Words.f91a77a0-a719-41c5-af36-35e0757f51ed.003.png)

Ahora seleccionaremos el tamaño del disco 

![](/assets/images/seguridad/almacenamiento_informacion_t7/Aspose.Words.f91a77a0-a719-41c5-af36-35e0757f51ed.004.png)

Una vez echo este le damos a crear y seleccionamos el disco que acabamos de crear .

![](/assets/images/seguridad/almacenamiento_informacion_t7/Aspose.Words.f91a77a0-a719-41c5-af36-35e0757f51ed.005.png)

![](/assets/images/seguridad/almacenamiento_informacion_t7/Aspose.Words.f91a77a0-a719-41c5-af36-35e0757f51ed.006.png)

Nos fijamos que se ha añadido correctamente .

![](/assets/images/seguridad/almacenamiento_informacion_t7/Aspose.Words.f91a77a0-a719-41c5-af36-35e0757f51ed.007.png)

**2.Particiona el disco utilizando el esquema MBR en cinco particiones de 40MB cada una. Utiliza el comando diskpart.**

Pulsamos las teclas windows + r  y escribimos diskpart

![](/assets/images/seguridad/almacenamiento_informacion_t7/Aspose.Words.f91a77a0-a719-41c5-af36-35e0757f51ed.008.png)

Le damos permisos de administrador 

![](/assets/images/seguridad/almacenamiento_informacion_t7/Aspose.Words.f91a77a0-a719-41c5-af36-35e0757f51ed.009.png)

Listamos los discos para saber cual tenemos que seleccionar 

![](/assets/images/seguridad/almacenamiento_informacion_t7/Aspose.Words.f91a77a0-a719-41c5-af36-35e0757f51ed.010.png)

Ahora seleccionamos el disco que queremos particionar en mi caso el 2 .

![](/assets/images/seguridad/almacenamiento_informacion_t7/Aspose.Words.f91a77a0-a719-41c5-af36-35e0757f51ed.012.png)


Introduciremos los  siguientes comandos para crear las particiones :

![](/assets/images/seguridad/almacenamiento_informacion_t7/Aspose.Words.f91a77a0-a719-41c5-af36-35e0757f51ed.011.png)

#![](/assets/images/seguridad/almacenamiento_informacion_t7/Aspose.Words.f91a77a0-a719-41c5-af36-35e0757f51ed.012.png)

#![](/assets/images/seguridad/almacenamiento_informacion_t7/Aspose.Words.f91a77a0-a719-41c5-af36-35e0757f51ed.011.png)

![](/assets/images/seguridad/almacenamiento_informacion_t7/Aspose.Words.f91a77a0-a719-41c5-af36-35e0757f51ed.013.png)

**3.Crea los un sistema de ficheros de tipo NTFS en la primera partición, FAT32 en la segunda y exFAT en la útima.**

Primero listamos las particiones 

![](/assets/images/seguridad/almacenamiento_informacion_t7/Aspose.Words.f91a77a0-a719-41c5-af36-35e0757f51ed.014.png)

Ahora le damos archivos a la primera partición para ello la seleccionamos y le damos formato  NTFS. 

![](/assets/images/seguridad/almacenamiento_informacion_t7/Aspose.Words.f91a77a0-a719-41c5-af36-35e0757f51ed.015.png)

Ahora vamos con la segunda partición que tendrá FAT32

![](/assets/images/seguridad/almacenamiento_informacion_t7/Aspose.Words.f91a77a0-a719-41c5-af36-35e0757f51ed.016.png)

Ahora la ultima  partición  EXFAT:

![](/assets/images/seguridad/almacenamiento_informacion_t7/Aspose.Words.f91a77a0-a719-41c5-af36-35e0757f51ed.017.png)

**4.Asigna letras de unidad consecutivas a partir de la letra M. Comprueba que puedes acceder a cada partición copiando un fichero en cada una.**

![](/assets/images/seguridad/almacenamiento_informacion_t7/Aspose.Words.f91a77a0-a719-41c5-af36-35e0757f51ed.018.png)

Probaremos a copiar archivos a cada partición para ver si nos deja 

![](/assets/images/seguridad/almacenamiento_informacion_t7/Aspose.Words.f91a77a0-a719-41c5-af36-35e0757f51ed.019.png)

![](/assets/images/seguridad/almacenamiento_informacion_t7/Aspose.Words.f91a77a0-a719-41c5-af36-35e0757f51ed.020.png)

![](/assets/images/seguridad/almacenamiento_informacion_t7/Aspose.Words.f91a77a0-a719-41c5-af36-35e0757f51ed.021.png)

A la letra P y O no podremos porque no tiene sistema de archivos 

**En la maquina  Debian**

**1. Agrega el disco creado en la primera parte a la maquina debian.**

Como hicimos al principio accedemos a configuración almacenamiento y seleccionamos nuestro disco  y comprobamos que se ha añadido 

![](/assets/images/seguridad/almacenamiento_informacion_t7/Aspose.Words.f91a77a0-a719-41c5-af36-35e0757f51ed.022.png)

**2.Con el comando fdisk, comprueba las particiones existentes en el disco** 

Como superusuario hacemos fdisk -l .

![](/assets/images/seguridad/almacenamiento_informacion_t7/Aspose.Words.f91a77a0-a719-41c5-af36-35e0757f51ed.023.png)

**3.Monta las particiones que ya están formateadas en el directorio /mnt/** 

He creado los siguientes directorios :

![](/assets/images/seguridad/almacenamiento_informacion_t7/Aspose.Words.f91a77a0-a719-41c5-af36-35e0757f51ed.024.png)

Para la primera partición  deberemos de instalarlos el paquete ntfs-3g

![](/assets/images/seguridad/almacenamiento_informacion_t7/Aspose.Words.f91a77a0-a719-41c5-af36-35e0757f51ed.025.png)

Montamos las  particiones :

![](/assets/images/seguridad/almacenamiento_informacion_t7/Aspose.Words.f91a77a0-a719-41c5-af36-35e0757f51ed.026.png)

**4.Comprueba que puedes acceder a los ficheros creados en Windows** 

Si , puedo acceder porque me he instalado el paquete anteriormente :

![](/assets/images/seguridad/almacenamiento_informacion_t7/Aspose.Words.f91a77a0-a719-41c5-af36-35e0757f51ed.027.png)

**5.Crea un sistema de ficheros ext3 en la tercera partición y otro de tipo xfs en la cuarta** 

Cambiaremos el sistemas de archivos de la primera a ext3

![](/assets/images/seguridad/almacenamiento_informacion_t7/Aspose.Words.f91a77a0-a719-41c5-af36-35e0757f51ed.028.png)

Ahora la cuarta le daremos ext4

![](/assets/images/seguridad/almacenamiento_informacion_t7/Aspose.Words.f91a77a0-a719-41c5-af36-35e0757f51ed.029.png)

**6.Monta ambas particiones y algún fichero de las otras.**

![](/assets/images/seguridad/almacenamiento_informacion_t7/Aspose.Words.f91a77a0-a719-41c5-af36-35e0757f51ed.030.png)

Voy a crear un fichero en la partición 3 y la llevaremos a la partición 4 

![](/assets/images/seguridad/almacenamiento_informacion_t7/Aspose.Words.f91a77a0-a719-41c5-af36-35e0757f51ed.031.png)

**7.Crea un nuevo disco virtual de 100MB y agrégalo a la MV**

\*Lo haré de 200 igual que antes para que me deje asignarle formato a las particiones .

Lo creamos igual  que anterior mente . Y comprobamos que se ha añadido 

![](/assets/images/seguridad/almacenamiento_informacion_t7/Aspose.Words.f91a77a0-a719-41c5-af36-35e0757f51ed.032.png)

Usamos fdisk

![](/assets/images/seguridad/almacenamiento_informacion_t7/Aspose.Words.f91a77a0-a719-41c5-af36-35e0757f51ed.033.png)

Creamos una tabla gpt 

![](/assets/images/seguridad/almacenamiento_informacion_t7/Aspose.Words.f91a77a0-a719-41c5-af36-35e0757f51ed.034.png)

Creamos las particiones y repetimos este paso 4 veces mas 

![](/assets/images/seguridad/almacenamiento_informacion_t7/Aspose.Words.f91a77a0-a719-41c5-af36-35e0757f51ed.035.png)

Y escribimos los cambios en los discos 

![](/assets/images/seguridad/almacenamiento_informacion_t7/Aspose.Words.f91a77a0-a719-41c5-af36-35e0757f51ed.036.png)

**8.Crea los sistemas sistemas de ficheros necesarios en cada una de las particiones.** 

Una vez creadas las particiones vamos a darle formato .

![](/assets/images/seguridad/almacenamiento_informacion_t7/Aspose.Words.f91a77a0-a719-41c5-af36-35e0757f51ed.037.png)

Las  particiones 3 y 4   las dejare sin sistema de archivos ya que inicialmente no tenían  . 

**9.Monta todas las particiones en /mnt/ y comprueba que puedes copiar ficheros.**

No se puede montar todas sobre el mismo directorio así que he creado unos debajo de mnt . Las particiones sin sistemas de archivos no se podrán  montar .

![](/assets/images/seguridad/almacenamiento_informacion_t7/Aspose.Words.f91a77a0-a719-41c5-af36-35e0757f51ed.038.png)

Creare un archivo de prueba y copiare a las particiones montadas .

![](/assets/images/seguridad/almacenamiento_informacion_t7/Aspose.Words.f91a77a0-a719-41c5-af36-35e0757f51ed.039.png)

**10.Muestra la salida de lsblk y lsblk -f**

![](/assets/images/seguridad/almacenamiento_informacion_t7/Aspose.Words.f91a77a0-a719-41c5-af36-35e0757f51ed.040.png)

![](/assets/images/seguridad/almacenamiento_informacion_t7/Aspose.Words.f91a77a0-a719-41c5-af36-35e0757f51ed.041.png)
