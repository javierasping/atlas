---
layout: single
title: ¿Como hacer copias de seguridad  en Windows Server 2019?
excerpt: "Practica de seguridad informatica del curso 2021/2022 , en esta se desarolla un escenario en el cual tienes que hacer diferentes tipos de copias de seguridad para comprobar su funcionamiento"
date: 2022-01-16
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

**Copias de seguridad en Windows**

Como sabemos, Windows 10/11 proporciona herramientas de respaldo para ayudarnos a crear copia de seguridad del sistema y los archivos de manera gratuita: la utilidad de Copia de Seguridad y Recuperación y Historial de archivos.

La utilidad Copia de Seguridad y Recuperación lo ayuda a crear una imagen del sistema, así como a hacer una copia de seguridad de otros archivos que necesita. El Historial de archivos se centra en hacer una copia de seguridad de sus archivos personales. Sin embargo, ninguno de ellos lo ayudará a realizar copias de seguridad incrementales o diferenciales. Para hacerlo, debe hacer uso de software de terceros.

Estas opciones son  útiles para un tipo de usuario domestico sin embargo para un entorno profesional o en servidores esto no es practico . 

Windows Server nos trae una característica propia la cual nos permite hacer copias de seguridad. 

**Instalación característica![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.001.png)**

Accedemos  a  Administración  del  servidor  >  Agregar  características  y  roles  ,  y seleccionamos la característica de copias de seguridad .

Una vez instalada esta característica podremos utilizar el programa de copias nativo de windows server  .

Para iniciar la aplicación utilizamos el buscador de windows  :

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.002.png)

Antes de esto crearemos es escenario previo a la realización del ejercicio , un directorio con tres ficheros :

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.003.png)

**Copia manual**

Haremos una copia completa del directorio para ello accedemos a hacer una copia una vez  y seleccionaremos la segunda opción : 

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.004.png)

Ahora seleccionaremos la raíz del el directorio que queremos hacer la copia de seguridad en mi caso este :

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.005.png)

En el segundo paso nos dirá donde queremos almacenar la copia , lo común en un entorno profesional es almacenarla en un nas o similar . Pero para realizar este ejercicio lo almacenare localmente :

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.006.png)

Una vez hecho estos pasos nos saldrá un pequeño resumen :

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.007.png)

Una vez le demos a copia de seguridad comenzara nuestra copia , la cual podemos comprobar que se ha creado en el destino :

**Programar copia** 

Seleccionamos programar copia , seleccionamos personalizada:

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.008.png)

Seleccionamos nuestro directorio que queremos hacerle una copia :

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.009.png)

A continuación seleccionamos la hora en que queremos que se realice:

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.010.png)

Ahora elegiremos donde almacenarla en mi caso la segunda opción :

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.011.png)

Ahora añadimos el volumen en el que guardaremos la copia :

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.012.png)

Nos saldrá el resumen de la copia y cuando le demos a finalizar quedara programada:

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.013.png)

Por ultimo nos mostrara cuando se realizara la primera copia de seguridad :

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.014.png)

Por desgracia esta característica de Microsoft no me permite seleccionar cuando realizar una copia completa , incremental o diferencial . Solo nos da una opción la cual cambia para SIEMPRE como hace la copia :![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.015.png)

Por lo que no puedo realizar la actividad con windows tendré que hacerla haciendo uso de un programa de terceros .

**Copias de seguridad en Windows con programa de terceros**

Para realizar estas copias voy a utilizar un software de terceros que es gratuito , este es Cobian. Este software  me  permitirá  crear  todas  las  variantes  de  copias  de  seguridad  así  como programarlas .También incluye la posibilidad de cifrar la copia y comprimila .

**Copias incrementales**

Crea una carpeta llamada datos con tres ficheros con distintos contenidos:

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.016.png)

**Dia 1**

Realiza una copia completa , para ello configurare una tarea :

-Seleccionando el origen y el destino :

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.017.png)

-Seleccionando el tipo de copia :

-Seleccionamos lanzar tarea :

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.018.png)

Se nos guardara en el directorio que hayamos indicado :

**Dia 2 ![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.019.png)**

Modifica el fichero1.txt, borra el fichero2.txt y crea un nuevo fichero fichero4.txt. Realiza una copia incremental 

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.020.png)

Ahora crearemos la tarea de copia incremental :

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.021.png)

Lanzamos la tarea y comprobamos que se ha creado :

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.022.png)

**Dia 3** 

Modifica el fichero3.txt y crea un nuevo fichero fichero5.txt.

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.023.png)

Realizamos una copa incremental :

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.024.png)

**Dia 4**

Crea un directorio carpeta1 y dentro crea un nuevo fichero fichero6.txt. 

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.025.png)

Realizamos una copia incremental y comprobamos que se haya creado :

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.026.png)

**Dia 5**

Borra el fichero1.txt y renombre la carpeta a carpeta2.

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.027.png)

Realizamos una copia incremental y comprobamos que se haya creado :

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.028.png)


**Dia 17****

Realiza una copia completa de el directorio .

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.029.png)

**Dia 7**

Crea otro directorio carpeta3 y dentro el fichero fichero6.txt. Borra el fichero4.txt

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.030.png)

Realizamos una copia incremental y comprobamos que se haya creado :

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.031.png)

Borra el fichero5.txt

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.032.png)

Realizamos una copia incremental del directorio :

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.033.png)

**Restaurar copias incrementales**

**Dia 3**

Para ello restauraremos las tres primeras copias y se nos quedaría el directorio así :

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.034.png)

Para ello restauraremos las 5 primeras copias , una vez restaurado quedaría así :

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.035.png)

**Dia 8**

Restauraremos la copia completa del día 6 y las incrementales posteriores a esta :

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.036.png)



**Copias diferenciales**

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.037.png)

**Dia 1**

Realiza una copia completa , para ello configurare una tarea : -Seleccionando el origen y el destino :

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.038.png)

-Seleccionando el tipo de copia :

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.039.png)



-Seleccionamos lanzar una copia completa cada 4 diferenciales para que coincida con el enunciado :

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.040.png)

Lanzamos la copia y se nos guardara en el directorio que hayamos indicado :

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.041.png)

**Dia 2** 

Modifica el fichero1.txt, borra el fichero2.txt y crea un nuevo fichero fichero4.txt. Realiza una copia incremental .

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.042.png)

Lanzamos la tarea y comprobamos que se ha creado :

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.043.png)


**Dia 20** 

Modifica el fichero3.txt y crea un nuevo fichero fichero5.txt.

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.044.png)

Realizamos una copa diferencial :

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.045.png)

**Dia 4**

Crea un directorio carpeta1 y dentro crea un nuevo fichero fichero6.txt. 

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.046.png)

Realizamos la tarea y comprobamos que se haya creado :

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.047.png)


**Dia 21**

Borra el fichero1.txt y renombre la carpeta a carpeta2.

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.048.png)

Realizamos una copia incremental y comprobamos que se haya creado :

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.049.png)

**Dia 6**

Realiza una copia completa de el directorio .

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.050.png)

**Dia 7**

Crea otro directorio carpeta3 y dentro el fichero fichero6.txt. Borra el fichero4.txt

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.051.png)



Realizamos una copia diferencial y comprobamos que se haya creado :

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.052.png)

**Dia 8**

Borra el fichero5.txt

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.053.png)

Realizamos una copia incremental del directorio :

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.054.png)



**Restaurar copias**

**Dia 3**

Una vez restaurada las 3 primeras copias nos quedaría un directorio con el siguiente contenido :

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.055.png)

**Dia 5**

Una vez restaurada las 5 primeras copias nos quedaría el directorio con el siguiente contenido :

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.056.png)

**Dia 8** 

Una vez restaurada la segunda completa y las 2 diferenciales posteriores nos quedaría así el directorio :

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.057.png)

**Copias mixtas** 

Para no alargar el documento , como ya he mostrado en este documento como hacer estas 3 tipos de copias . Pasare directamente a restaurar las mismas .

**Restauración copias mixtas Dia 3**

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.034.png)

**Dia 5**

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.058.png)

**Dia 8**

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.059.png)

**¿Ocupan más las copias diferenciales o las copias incrementales?**

Según mis copias pesan mas las diferenciales ya que consiste en copiar todos los datos nuevos o modificados desde la última copia completa.

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.060.png)

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.061.png)

**Automatización de copias de seguridad**

El mismo programa con las tareas que he creado anteriormente para la realización de los ejercicios nos permite programar las copias :

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.062.png)

Ademas en la misma aplicación nos permite configurar el envió de correos para recibir el estado de la tarea para así evitarnos comprobar diariamente el estados de las tareas accediendo al servidor  y facilitándolo con un simple vistazo al correo :

![](/assets/images/seguridad/copiasdeseguridadwin/Aspose.Words.f2457733-db51-4433-a67d-46472fbcad76.063.png)

