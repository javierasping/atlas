---
layout: single
title: ¿Como montar un drupal en debian 11?
excerpt: "Explicacion basica de como montar el CMS drupal en debian 11 "
date: 2022-03-14
classes: wide
header:
  teaser: /assets/images/prueba/logo.png
  teaser_home_page: true
  icon: /assets/images/logo.jpg
categories:
  - Aplicaciones web
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
</script>﻿

INSTALACIÓN CMS DRUPAL APLICACIONES WEB


**Requisitos previos** 

Para realizar la instalación de Drupal necesitaremos tener instalada una pila LAMP . Puedes seguir este [enlace](https://franciscojaviercrucesdoval.wordpress.com/2022/01/17/instalacion-lamp-en-debian-11/?preview_id=481&preview_nonce=1725acbc56&preview=true) .

**Instalación**

Lo primero que haremos será descargarnos desde lo repositorios oficiales drupal :

![](/assets/images/aw/drupal/Aspose.Words.c0d04704-8ca1-45a6-90e8-8e84c8cfc05e.001.png)

**Creación de directorios**

Ahora vamos a crear los siguientes directorios que utilizara nuestro sitio , podemos hacerlo descomprimiendo el archivo que acabamos de descargar :

![](/assets/images/aw/drupal/Aspose.Words.c0d04704-8ca1-45a6-90e8-8e84c8cfc05e.002.png)

Puede ser interesante crear un enlace simbólico sin números para facilitar la instalación y el mantenimiento:

![](/assets/images/aw/drupal/Aspose.Words.c0d04704-8ca1-45a6-90e8-8e84c8cfc05e.003.png)

Como Drupal necesita escribir en su directorio de instalación, permisos al usuario con el que corre el servicio web:

![](/assets/images/aw/drupal/Aspose.Words.c0d04704-8ca1-45a6-90e8-8e84c8cfc05e.004.png)

**Creación base de datos**

Nos conectamos al servicio de base de datos :

![](/assets/images/aw/drupal/Aspose.Words.c0d04704-8ca1-45a6-90e8-8e84c8cfc05e.005.png)

Creamos la base de datos para Drupal:

![](/assets/images/aw/drupal/Aspose.Words.c0d04704-8ca1-45a6-90e8-8e84c8cfc05e.006.png)

Creamos el usuario que trabajará con dicha base:

![](/assets/images/aw/drupal/Aspose.Words.c0d04704-8ca1-45a6-90e8-8e84c8cfc05e.007.png)

Concedemos suficientes privilegios al usuario sobre la base:

![](/assets/images/aw/drupal/Aspose.Words.c0d04704-8ca1-45a6-90e8-8e84c8cfc05e.008.png)

Refrescamos la tabla de permisos:

![](/assets/images/aw/drupal/Aspose.Words.c0d04704-8ca1-45a6-90e8-8e84c8cfc05e.009.png)

Y ya podemos cerrar la sesión:

![](/assets/images/aw/drupal/Aspose.Words.c0d04704-8ca1-45a6-90e8-8e84c8cfc05e.010.png)

**Servicio web**

Vamos a crear un sitio virtual para nuestro wordpress podemos copiar el archivo por defecto y editarlo :

![](/assets/images/aw/drupal/Aspose.Words.c0d04704-8ca1-45a6-90e8-8e84c8cfc05e.011.png)

Dentro del fichero añadimos las siguientes líneas :

![](/assets/images/aw/drupal/Aspose.Words.c0d04704-8ca1-45a6-90e8-8e84c8cfc05e.012.png)

Ahora crearemos un enlace simbólico :

![](/assets/images/aw/drupal/Aspose.Words.c0d04704-8ca1-45a6-90e8-8e84c8cfc05e.013.png)

Y cargamos el módulo *Rewrite* de Apache:

![](/assets/images/aw/drupal/Aspose.Words.c0d04704-8ca1-45a6-90e8-8e84c8cfc05e.014.png)

Ahora reiniciamos apache :

![](/assets/images/aw/drupal/Aspose.Words.c0d04704-8ca1-45a6-90e8-8e84c8cfc05e.015.png)

**PHP**

Drupal requiere la presencia en Debian 11 de ciertas extensiones que instalaremos :

![](/assets/images/aw/drupal/Aspose.Words.c0d04704-8ca1-45a6-90e8-8e84c8cfc05e.016.png)

Una vez instaladas recargamos apache :

![](/assets/images/aw/drupal/Aspose.Words.c0d04704-8ca1-45a6-90e8-8e84c8cfc05e.017.png)

**Instalador web**

Ahora accederemos al instalador web introduciendo la IP de nuestra máquina seguida de lo siguiente , una vez introducimos podemos seleccionar el idioma :

![](/assets/images/aw/drupal/Aspose.Words.c0d04704-8ca1-45a6-90e8-8e84c8cfc05e.018.png)

Seleccionaremos la versión que queramos en mi caso estándar :

![](/assets/images/aw/drupal/Aspose.Words.c0d04704-8ca1-45a6-90e8-8e84c8cfc05e.019.png)

Rellenamos los campos con los datos introducidos anteriormente en la instalación :

![](/assets/images/aw/drupal/Aspose.Words.c0d04704-8ca1-45a6-90e8-8e84c8cfc05e.020.jpeg)

Comenzará la instalación:

![](/assets/images/aw/drupal/Aspose.Words.c0d04704-8ca1-45a6-90e8-8e84c8cfc05e.021.png)

Una vez finalice deberemos de configurar nuestro sitio :

![](/assets/images/aw/drupal/Aspose.Words.c0d04704-8ca1-45a6-90e8-8e84c8cfc05e.022.png)

Ahora esperamos a que se apliquen las configuraciones :

![](/assets/images/aw/drupal/Aspose.Words.c0d04704-8ca1-45a6-90e8-8e84c8cfc05e.023.png)

Cuando finalice así quedaría nuestro sitio :

![](/assets/images/aw/drupal/Aspose.Words.c0d04704-8ca1-45a6-90e8-8e84c8cfc05e.024.png)

**Añadir usuarios**

Al igual que otros CMS ,este también cuanto con distintos roles para los usuarios así que vamos a crear un usuario para cada rol. Para esto accedemos a Inicio>Administración > Usuarios .       

A continuación rellenamos el siguiente formulario con los datos de nuestro usuario:

![](/assets/images/aw/drupal/Aspose.Words.c0d04704-8ca1-45a6-90e8-8e84c8cfc05e.025.png)

Podemos ver que he creado 1 usuario con cada posibilidad :

![](/assets/images/aw/drupal/Aspose.Words.c0d04704-8ca1-45a6-90e8-8e84c8cfc05e.026.png)

Si no nos convence estos roles predefinidos podemos editarlos en la pestaña roles y personalizarlos o crear los nuestros propios :

![](/assets/images/aw/drupal/Aspose.Words.c0d04704-8ca1-45a6-90e8-8e84c8cfc05e.027.png)

**Cambiar tema**

Para cambiar el tema por defecto tenemos que venir a Inicio > Administración >  apariencia . Una vez aquí podemos instalarlo buscando el tema que nos guste bajando y dándole a instalar :

![](/assets/images/aw/drupal/Aspose.Words.c0d04704-8ca1-45a6-90e8-8e84c8cfc05e.028.png)

O añadiéndolo desde una URL o el archivo descargado localmente :

![](/assets/images/aw/drupal/Aspose.Words.c0d04704-8ca1-45a6-90e8-8e84c8cfc05e.029.png)

Una vez lo hemos añadido debemos de buscarlo en la sección de instalados y darle a configurar como predeterminado :

![](/assets/images/aw/drupal/Aspose.Words.c0d04704-8ca1-45a6-90e8-8e84c8cfc05e.030.jpeg)

Si lo hemos hecho bien nos saldrá el siguiente mensaje :

![](/assets/images/aw/drupal/Aspose.Words.c0d04704-8ca1-45a6-90e8-8e84c8cfc05e.031.png)

**Instalar un módulo**

Accedemos a Inicio>Administración > Entender y nos descargamos desde drupal.org el módulo que deseemos , lo seleccionamos y lo subimos :

![](/assets/images/aw/drupal/Aspose.Words.c0d04704-8ca1-45a6-90e8-8e84c8cfc05e.032.png)

Le damos a continuar y nos saldrá lo siguiente :

![](/assets/images/aw/drupal/Aspose.Words.c0d04704-8ca1-45a6-90e8-8e84c8cfc05e.033.png)

A continuación buscamos en la sección ampliar nuestro módulo y lo seleccionamos :

![](/assets/images/aw/drupal/Aspose.Words.c0d04704-8ca1-45a6-90e8-8e84c8cfc05e.034.png)

Bajamos y le damos a instalar :

![](/assets/images/aw/drupal/Aspose.Words.c0d04704-8ca1-45a6-90e8-8e84c8cfc05e.035.png)

Si todo ha ido bien nos saldrá el siguiente mensaje :

![](/assets/images/aw/drupal/Aspose.Words.c0d04704-8ca1-45a6-90e8-8e84c8cfc05e.036.png)

**Instalar un foro**

Para esto viene un módulo por defecto llamado Fórum así que lo instalamos como en el apartado anterior :

![](/assets/images/aw/drupal/Aspose.Words.c0d04704-8ca1-45a6-90e8-8e84c8cfc05e.037.png)

Si accedemos a estructura nos saldrá el apartado foros :

![](/assets/images/aw/drupal/Aspose.Words.c0d04704-8ca1-45a6-90e8-8e84c8cfc05e.038.png)

Nos saldrán los distintos foros que tenemos , como está recién instalado solo viene el predeterminado :

![](/assets/images/aw/drupal/Aspose.Words.c0d04704-8ca1-45a6-90e8-8e84c8cfc05e.039.png)

Para acceder a él podemos poner un enlace en los menús o escribir /forum:

![](/assets/images/aw/drupal/Aspose.Words.c0d04704-8ca1-45a6-90e8-8e84c8cfc05e.040.png)

**Seguridad de usuarios y backups**

Para tener control de los usuarios podemos instalar módulos como Login Security que nos da la opción de modificar opciones a la hora de que un usuario se registre , el número máximo de intentos que un usuario puede realizar para registrarse en nuestro sitio, bloquear determinadas cuentas ya sea por usuario o por IP de manera temporal o definitiva.

Otro módulo interesante es Password Policy la cual nos permite personalizar nuestra política de contraseña para que los usuarios estén obligados a tener contraseñas seguras .

Además de estas dos hay una infinidad de módulos desarrollados para aumentar la seguridad de nuestro sitio , pero estos dos son los más sencillos que he encontrado .

Para copias de seguridad , hay tenemos uno por defecto llamado Backup and migrate que nos permite crear copias de seguridad manualmente o programándolas que es muy útil para evitar la perdida de información .

