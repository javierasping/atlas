---
layout: single
title: Scripts administracion usuarios y grupos locales  active directory
excerpt: "Scripts basicos de ejemplo para administrar usuarios y grupos locales de active directory en Windows Server 2019"
date: 2022-11-12
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


**Usuarios y grupos locales**

1. Crear un script de PowerShell que realice las siguientes tareas (script1.ps1)
1. Crear un usuario llamado “usuloc01”, sin contraseña y que esté deshabilitado.
1. Habilitar el usuario “usuloc01”
1. Modificar la descripción del usuario “usuloc01” para que tenga el texto “Descripción usuario de prueba”.
1. Crear otro usuario llamado “usuloc02” con contraseña (habilitado).
1. Crear otro usuario llamado “usuloc03” con contraseña y que se cree deshabilitado.
1. Crear un nuevo grupo local llamado “grptest01”.
1. Crear otro grupo llamado “grpsegundo”.
1. Cambiar el nombre del grupo “grptest01” por “grpprimero”.
1. Modificar el grupo “grpprimero” y añadirle la descripción “Este es el primer grupo local”.
1. Añadir los usuarios “usuloc01” y “usuloc02” al grupo “grpprimero”
1. Añadir el usuario “usuloc03” al grupo “grpsegundo”.
1. Obtener/mostrar los miembros del grupo “grpprimero”
1. Eliminar el usuario “usuloc02” del grupo “grpprimero”.
1. Eliminar el grupo “grpsegundo”.
1. Eliminar el usuario “usuloc03”.

![](/assets/images/sistemas/Aspose.Words.43b37f75-4741-4aa3-b896-5df7106b447f.001.png)

**Administrar objetos del dominio**

2. Crear un script de PowerShell que realice las siguientes tareas (script2.ps1).
1. Crear una unidad organizativa llamada “ciclosmr”.
1. Crear otra unidad organizativa llamada “cicloasir”.
1. Dentro de la UO “ciclosmr” crear otras dos unidades organizativas, llamadas “primerosmr” y “segundosmr”
1. Crear un grupo llamado “sistemas” dentro de la UO “primerosmr” (recuerda que está dentro de la UO “ciclosmr”).
1. Crear otro grupo llamado “equipos” dentro de la UO “primerosmr”.
1. Crear un usuario llamado “Alfonso”, con contraseña y habilitado.
1. Crear otro usuario llamado “Manuel”, con contraseña, pero que esté deshabilitado.
1. Habilitar la cuenta de usuario “Manuel”.
1. Borrar el usuario “Manuel”.
1. Crear los usuarios “Marta” y “Antonio”, con contraseña y habilitados.
1. Añadir al grupo “sistemas” los usuarios Marta y Antonio.
1. Añadir al grupo “equipos” el usuario Alfonso.
1. Eliminar del grupo “sistemas” al usuario Antonio.
1. Mover a la Unidad Organizativa “cicloasir” el usuario “Alfonso”.
1. Crear otro usuario llamado “Teresa”, con contraseña, habilitado y que se cree directamente en la Unidad Organizativa “ciclosmr”.
1. Permitir el borrado accidental de la UO “cicloasir”.

![](/assets/images/sistemas/Aspose.Words.43b37f75-4741-4aa3-b896-5df7106b447f.002.png)

**Script**

3. Crear un script (script3.ps1) que muestre un menú al usuario y le permita realizar distintas operaciones con usuarios y grupos. Utiliza como base el archivo “menu\_usuarios\_grupos\_AD.ps1”. Vamos a suponer que el usuario siempre introduce valores correctos, no es necesario controlar posibles campos vacíos, nombres erróneos, objetos inexistentes, etc.

![](/assets/images/sistemas/Aspose.Words.43b37f75-4741-4aa3-b896-5df7106b447f.003.png)

![](/assets/images/sistemas/Aspose.Words.43b37f75-4741-4aa3-b896-5df7106b447f.004.png)

\*Los start-sleep los he puesto para que se vea el ultimo mensaje .

**Estructura**

4.Realizar un script que cree la siguiente estructura en Directorio Activo:

![](/assets/images/sistemas/Aspose.Words.43b37f75-4741-4aa3-b896-5df7106b447f.005.png)

