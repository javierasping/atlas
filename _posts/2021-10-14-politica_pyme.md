---
layout: single
title: Plan director de seguridad
excerpt: "Un Plan Director de Seguridad consiste en la definición y priorización de un conjunto de proyectos en materia de seguridad de la información con el objetivo de reducir los riesgos a los que está expuesta la or- ganización hasta unos niveles aceptables, a partir de un análisis de la situación inicial."
date: 2022-11-12
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
Ejemplo plan director de seguridad
**Introducción** 

El sector de la educación engloba todo tipo de organizaciones que se dedican a la enseñanza . La implantación de nuevas tecnologías es importante en este tipo de instituciones y empresas . En las cuales se hace un uso intensivo de equipos informáticos en las cuales se almacenan datos de las personas que se matriculan para aprender y en ocasiones estos datos pueden ser especialmente protegidos como es el caso de menores de edad o de salud 

**Selección de la empresa**

Este plan estará dirigido a un centro educativo como puede ser nuestro centro el IES Gonzalo Nazareno . El cual tiene una gran cantidad de usuarios , maquinas y servidores . He elegido este para tener una referencia real . 

**Objetivos** 

- Evaluar la situación para identificar los riesgos sobre la seguridad en el centro
- Identificar que áreas del centro  son las mas expuestas a estos riesgos en función del impacto y la probabilidad de que ocurra 
- Adoptar las medidas necesarias para minimizar estos riesgos 

**Fases del documento**

1. Definición de los activos 
1. Valoración de los activos 
1. Amenazas de los activos
1. Impacto de las amenazas en los  activos
1. Plan de prevención  de riesgos 
1. Plan de contingencia 

**1.Definición de los activos** 

Activos son los conocimientos o datos que tiene valor para una organización , mientras que en la misma norma , los sistemas de información comprenden a las aplicaciones , servicios , activos de las tecnologías de información u otros componentes que permiten el manejo de la misma .

**Equipos informáticos (Hardware)**

Aquellos que se encargan de realizar una función a los distintos usuarios del centro :

- Servidores 
  - Conjunto de servidores en  varios formatos tanto como en armarios rack como en torres de sobremesa los cuales se utilizan para albergar servicios utilizados por los usuarios del centro así como también  para formar a los alumnos de grado superior (ASIR)
- Ordenadores personales 
  - Dispositivos los cuales utilizan alumnado y profesorado para desempeñar  diversas tareas 
- Router
  - Equipo encargado de suministrar al centro conexión a internet 
- Switch
  - Encargado de dar conexión a  los distintos dispositivos de forma cableada 
- Puntos de acceso
  - Encargado de dar conexión a internet a los distintos dispositivos de manera inalámbrica 
- Impresoras 
  - Encargadas de imprimir los distintos documentos que el profesorado necesita .
- Escáneres
  - Encargados de digitalizar los distintos documentos que el profesorado quiere conservar de manera digital 
- SAI
  - Equipo auxiliar para apagar correctamente los servidores ante caída del suministro eléctrico
- Cables
  - Medio de transmisión cableado se usa fibra y utp cat 6

**Almacenamiento de la  información** 

Son los distintos dispositivos o archivos donde se guarda la información :

- Unidades USB
  - Dispositivos los cuales pueden albergar documentos tanto del profesorado como del alumnado 
- Discos duros internos
  - Guardan información importante como documentos confidenciales , trabajos del alumnado ...
- Discos duros externos 
  - Utilizado por los usuarios del centro para transportar información 
- Documentos impresos 
  - Información almacenada de forma física que pude contener datos confidenciales 

**Usuarios del centro** 

Personas o grupo de personas  las cuales utilizan los equipos informáticos del centro :

- Equipo directivo 
  - Es el máximo régimen administrativo del centro el cual puede acceder a cualquier información o lugar .
- Jefes de departamento 
  - Es el que lidera a un grupo de profesores , este acceder a toda la información de los alumnos de los profesores que lidera . 
- Profesorado
  - Encargados de formar a los alumnos , estos solo pueden acceder a la información a los cuales les da clase .
- Conserjes y Secretarias 
  - Encargados de dar servicio tanto a profesores como a alumnado , pueden tratar con datos confidenciales  puntualmente .
- Alumnado 
  - Usuario con privilegios  mas bajo del centro el cual solo puede acceder a determinados lugares y equipos determinados .
- Personal de limpieza
  - Equipo de personas encargadas de mantener limpio el centro las cuales acceden a todas las instalaciones .

**Aplicaciones** 

Software utilizado por los usuarios del centro 

- Moodle 
  - Plataforma educativa del centro
- Navegadores web 
  - Utilizados para navegar por la red 
- Telegram
  - Medio de comunicación de los profesores 
- Windows 10 
  - Sistema operativo utilizado principalmente 
- Debian 10-11
  - Sistema operativo utilizado principalmente 
- Programas de ofimática :
  - Aplicaciones de edición de fotografiá 
  - Aplicaciones de edición de video 
  - Sistemas gestiones de base de datos  
  - Editores de texto 
  - Editores de presentaciones 
  - Hojas de calculo 
- Nube 
  - Servicio Online que permite acceder a los archivos teniendo conexión a internet 

**Datos**

Información valiosa y en varios casos confidencial 

- Evaluaciones de los alumnos 
  - Informes que generan los profesores sobre los alumnos 
- Matriculas de los alumnos 
  - Inscripción de los alumnos en el centro 
- Listado de los alumnos 
  - Serie ordenada de nombre 
- Exámenes 
  - Prueba evaluable   de los alumnos 
- Fichas del profesorado 
  - Datos personales del profesorado 
- Facturas 
  - Compras y gatos realizados  por el centro 

**Servicios** 

Aquellos que satisfacen las necesidades del usuario 

- Internet 
  - Conexión contratada con movistar 
- DHCP
  - Asignación de ips dinámica 
- DNS
  - Servicio de resolución de nombres propio que tiene el centro llamado macaco 
- FTP
  - Servidor nas para compartir archivos en el centro  
- Servidor de correo electrónico
  - Para gestionar los diferentes servicios del centro 

**2.Valoración de los activos**

Para tener en cuenta los activos mas valiosos hay que clasificarlos en función de su importancia , esta calificación se le da en función de la repercusión que un  daño  puede causar  al centro . 

Se calificara las siguientes características :  

**Disponibilidad (D) :**

Garantiza que el sistema y los datos estarán disponible para los usuarios . 

**Integridad (I):**

Garantiza que la información no ha sido modificada sin autorización . 

**Confidencialidad (C):**

Garantiza que el acceso a la información no se produce de forma no autorizada . 

**No repudio (R) :**

Impide que el emisor niegue haber estado involucrado en una interacción .



|`  `**Valoración** **estimada numérica** |
| - |
|**Activo**|**(D)**|**(I)**|**(C)**|**(R)**|
|Servidores |10 |10|-||
|Ordenadores personales |9|10|-||
|Router |9|6|-||
|Switches |9|-|-||
|Puntos de acceso |9|-|-||
|Impresoras |2|-|-||
|Escáneres |2|-|-||
|SAI |7|-|-||
|Cables  |9|-|-||
|Unidades USB |4|2|7||
|Discos duros internos |8|8|9||
|Discos duros externos |8|8|9||
|Documentos impresos |8|8|9||
|Moodle |9|10|-||
|Navegadores web |7|-|-||
|Telegram |6|7|9||
|Windows 10 |10|-|-||
|Debian 10-11 |10|-|-||
|Programas de ofimática |6|-|-||

|Nube |5|7|9||
| - | - | - | - | :- |
|Evaluaciones de los alumnos |5|8|9||
|Matriculas de los alumnos |2|5|9||
|Listado de los alumnos |5|5|9||
|Exámenes |6|9|9||
|Fichas del profesorado |5|5|9||
|Facturas |3|8|9||
|Internet |10|-|-||
|DHCP |7|-|-||
|DNS |7|-|-||
|FTP |4|-|-||
|Servidor de correo electrónico |4|-|-||
**Escala de valores** 



|**Valor**|**Gravedad**|
| - | - |
|0|Nulo|
|1-4|Daño leve|
|5-7|Daño medio|
|8-10|Daño alto |
|-|No evaluable|

**3.Amenazas de los  activos** 

Una amenaza es la posible aparición de daños a cualquier activo del centro

Ambientales



|**Incendios**|
| - |
|<p>**Activos afectados:**</p><p>- Equipos informáticos (Hardware)</p><p>- Almacenamiento de la  información </p><p>- Aplicaciones </p><p>- Datos </p><p>- Servicios</p>|<p>**Características afectadas :**</p><p>- Disponibilidad</p><p>- Integridad</p>|
|El fuego puede acabar calcinando nuestros recursos total o parcialmente , impidiendo el acceso temporalmente a nuestros recursos .|

|**Inundaciones**|
| - |
|<p>**Activos afectados:**</p><p>- Equipos informáticos (Hardware)</p><p>- Almacenamiento de la  información </p><p>- Aplicaciones </p><p>- Datos </p><p>- Servicios</p>|<p>**Características afectadas :**</p><p>- Disponibilidad</p><p>- Integridad</p>|
|El agua puede acabar rompiendo nuestros recursos total o parcialmente , impidiendo el acceso temporalmente a nuestros recursos .|


|**Terremotos**|
| - |
|<p>**Activos afectados:**</p><p>- Equipos informáticos (Hardware)</p><p>- Almacenamiento de la  información </p><p>- Aplicaciones </p><p>- Datos </p><p>- Servicios</p>|<p>**Características afectadas :**</p><p>- Disponibilidad</p><p>- Integridad</p>|
|Los seísmos pueden causar daños en la estructura del edificio , derribandolo en casos graves .|


|**Suciedad**|
| - |
|<p>**Activos afectados:**</p><p>- Equipos informáticos (Hardware)</p><p>- Almacenamiento de la  información </p><p>- Aplicaciones </p><p>- Datos </p><p>- Servicios</p>|<p>**Características afectadas :**</p><p>- Disponibilidad</p><p>- Integridad</p>|
|El polvo acumulado puede provocar el aumento de las temperaturas en nuestros equipos o dañar componentes como un disco duro |
**Tecnológico** 



|**Corte del suministro eléctrico**|
| - |
|<p>**Activos afectados:**</p><p>- Equipos informáticos (Hardware)</p><p>- Almacenamiento de la  información </p><p>- Aplicaciones </p><p>- Datos </p><p>- Servicios</p>|<p>**Características afectadas :**</p><p>• Disponibilidad</p>|
|El corte de alimentación puede ser provocado por la averiá de un transformador o generador eléctrico . Ademas puede hacer que se estropeen componentes |

|**Temperaturas muy altas o bajas** |
| - |
|<p>**Activos afectados:**</p><p>- Equipos informáticos (Hardware)</p><p>- Almacenamiento de la  información </p><p>- Aplicaciones </p><p>- Servicios</p>|<p>**Características afectadas :**</p><p>• Disponibilidad</p>|
|La mala aclimatación puede provocar que nuestros equipos no rindan .|


|**Averiás**|
| - |
|<p>**Activos afectados:**</p><p>- Equipos informáticos (Hardware)</p><p>- Almacenamiento de la  información </p>|<p>**Características afectadas :**</p><p>- Disponibilidad</p><p>- Integridad </p>|
|Fallos en los equipos debido al uso . Puede ser debido a un defecto de fabrica o por el uso del dispositivo . |


|**Infecciones por código malicioso**|
| - |
|<p>**Activos afectados:**</p><p>- Equipos informáticos (Hardware)</p><p>- Almacenamiento de la  información </p><p>- Aplicaciones </p><p>- Datos </p><p>- Servicios</p>|<p>**Características afectadas :**</p><p>- Disponibilidad</p><p>- Integridad</p><p>- Confidencialidad </p><p>- No repudio</p>|
|A través de equipos de trabajo o dispositivos móviles , en su mayoría a través del correo electrónico .Una vez infectados pasamos a entrar en una botnet.|


|**Intrusiones**|
| - |
|<p>**Activos afectados:**</p><p>- Equipos informáticos (Hardware)</p><p>- Almacenamiento de la  información </p><p>- Aplicaciones </p><p>- Datos </p><p>- Servicios</p>|<p>**Características afectadas :**</p><p>- Disponibilidad</p><p>- Integridad</p><p>- Confidencialidad </p><p>- No repudio</p>|
|Se provocan a través de vulnerabilidades de nuestro software , se realizan a través de exploits|


|**Ataques DDoS** |
| - |
|<p>**Activos afectados:**</p><p>- Almacenamiento de la  información </p><p>- Aplicaciones </p><p>- Datos </p><p>- Servicios</p>|<p>**Características afectadas :**</p><p>- Disponibilidad</p><p>- No repudio</p>|
|` `Afectan a varios recursos de la organización y impiden el normal funcionamiento de los mismos|


|**Ransomware**|
| - |
|<p>**Activos afectados:**</p><p>- Equipos informáticos (Hardware)</p><p>- Almacenamiento de la  información </p><p>- Aplicaciones </p><p>- Datos </p><p>- Servicios</p>|<p>**Características afectadas :**</p><p>- Disponibilidad</p><p>- Integridad</p><p>- Confidencialidad </p><p>- No repudio</p>|
|Es un software que pueden borrar , modificar o encriptar nuestros datos y pueden estar provocados de forma intencionada para sacar rédito económico . |
**Humanos**  



|**Hurto**|
| - |
|<p>**Activos afectados:**</p><p>- Equipos informáticos (Hardware)</p><p>- Almacenamiento de la  información </p><p>- Datos </p>|<p>**Características afectadas :**</p><p>- Disponibilidad</p><p>- Integridad </p><p>- Confidencialidad </p><p>- No repudio </p>|
|El robo de hardware por parte de un tercero.|


|**Adulteración** |
| - |
|<p>**Activos afectados:**</p><p>- Almacenamiento de la  información </p><p>- Aplicaciones </p><p>- Datos </p><p>- Servicios</p>|<p>**Características afectadas :**</p><p>- Disponibilidad</p><p>- Integridad</p><p>- No repudio </p>|
|Usuario que al usar un determinado servicio  , modifica o elimina un archivo por error |


|**Fraude**|
| - |
|<p>**Activos afectados:**</p><p>• Datos </p>|<p>**Características afectadas :**</p><p>- Disponibilidad</p><p>- Integridad</p><p>- Confidencialidad</p>|
|Modificar programas o archivos a los cual el usuario no esta autorizado a hacer |


|**Modificación**|
| - |
|<p>**Activos afectados:**</p><p>- Aplicaciones </p><p>- Datos </p><p>- Servicios</p>|<p>**Características afectadas :**</p><p>• Disponibilidad</p>|
|Los seísmos pueden causar daños en la estructura del edificio , derribandolo en casos graves .|

|**Errores del administrador**|
| - |
|<p>**Activos afectados:**</p><p>- Aplicaciones </p><p>- Datos </p><p>- Servicios</p>|<p>**Características afectadas :**</p><p>- Disponibilidad</p><p>- Integridad</p><p>- Confidencialidad</p><p>- No repudio </p>|
|Un administrador puede cometer graves errores que pongan en peligro gran cantidad de servicios |


|**Revelación**|
| - |
|<p>**Activos afectados:**</p><p>- Aplicaciones </p><p>- Datos </p><p>- Servicios</p>|<p>**Características afectadas :**</p><p>- Confidencialidad </p><p>- No repudio </p>|
|La revelación de  información confidencial a personas no autorizadas |


|**Perdida de la información** |
| - |
|<p>**Activos afectados:**</p><p>- Aplicaciones </p><p>- Datos </p><p>- Servicios</p>|<p>**Características afectadas :**</p><p>- Disponibilidad</p><p>- Integridad</p>|
|Perdida de información voluntaria o involuntariamente |


|**Sabotaje**|
| - |
|<p>**Activos afectados:**</p><p>- Almacenamiento de la  información </p><p>- Aplicaciones </p><p>- Datos </p><p>- Servicios</p>|<p>**Características afectadas :**</p><p>- Disponibilidad</p><p>- Integridad </p><p>- Confidencialidad</p><p>- No repudio</p>|
|Daño o destrucción que se hace intencionadamente en un servicio como forma de lucha o protesta contra el organismo que los dirige o bien como método para beneficiar a una persona o grupo que es contrario a dicho organismo.|


|**Vandalismo**|
| - |
|<p>**Activos afectados:**</p><p>- Equipos informáticos (Hardware)</p><p>- Almacenamiento de la  información </p><p>- Aplicaciones </p><p>- Datos </p><p>- Servicios</p>|<p>**Características afectadas :**</p><p>- Disponibilidad</p><p>- Integridad</p><p>- Confidencialidad </p><p>- No repudio</p>|
|El vandalismo destruye o profana bienes de la empresa . Generalmente para atacar a su imagen |

|**Craker / Hacker**|
| - |
|<p>**Activos afectados:**</p><p>- Equipos informáticos (Hardware)</p><p>- Almacenamiento de la  información </p><p>- Aplicaciones </p><p>- Datos </p><p>- Servicios</p>|<p>**Características afectadas :**</p><p>- Disponibilidad</p><p>- Integridad</p><p>- Confidencialidad </p><p>- No repudio</p>|
|Persona con grandes conocimientos en informática que accede de forma fraudulenta a sistemas informáticos con fines de manipularlo .|


|**Falsificación** |
| - |
|<p>**Activos afectados:**</p><p>- Aplicaciones </p><p>- Datos </p><p>- Servicios</p>|<p>**Características afectadas :**</p><p>- Integridad</p><p>- Confidencialidad </p><p>- No repudio</p>|
|Falsificación de documentos , paginas web … |


|**Robo de contraseñas** |
| - |
|<p>**Activos afectados:** </p><p>- Aplicaciones </p><p>- Datos </p><p>- Servicios</p>|<p>**Características afectadas :**</p><p>- Disponibilidad</p><p>- Integridad</p><p>- Confidencialidad </p><p>- No repudio</p>|
|` `Obtención de credenciales de los usuarios .|


|**Phishing**|
| - |
|<p>**Activos afectados:**</p><p>- Equipos informáticos (Hardware)</p><p>- Almacenamiento de la  información </p><p>- Datos </p>|<p>**Características afectadas :**</p><p>- Disponibilidad</p><p>- Integridad </p><p>- Confidencialidad </p><p>- No repudio </p>|
|Un ataque para engañarle y hacer que comparta contraseñas, números de tarjeta de crédito, y otra información confidencial haciéndose pasar por una institución de confianza en un mensaje de correo electrónico o llamada telefónica .|
**4.Impacto de las amenazas en los  activos**



|**Valor**|**Gravedad**|
| - | - |
|0|Nulo|
|1-4|Asumible|
|5-7|Importante|
|8-10|Intolerable|
|-|No evaluable|
**Ambientales**



|**Amenaza** |**Gravedad** |**Probabilidad**|**Impacto**|
| - | - | - | - |
|Incendios |9|20%|9|
|Inundaciones|7|10%|7|
|Terremotos |7|10%|6|
|Suciedad |2|35%|2|
**Tecnológico**



|**Amenaza** |**Gravedad** |**Probabilidad**|**Impacto**|
| - | - | - | - |
|Corte del suministro eléctrico |10|80%|10|
|<p>Temperaturas muy altas </p><p>o bajas </p>|4|10%|3|
|Averiás |5|30%|4|
|Infecciones por código malicioso |10|60%|9|
|Intrusiones|7|25%|7|
|Ataques DDos|8|80%|6|
|Ransomware|10|60%|9|
**Humanos** 



|**Amenaza** |**Gravedad** |**Probabilidad**|**Impacto**|
| - | - | - | - |
|Hurto |4|20%|3|
|Adulteración |8|30%|7|
|Fraude |9|20%|8|
|Modificación |7|30%|6|
|Errores del administrador |8|10%|7|
|Revelación |6|20%|5|
|Perdida de información|7|40%|6|
|Sabotaje |4|1%|3|
|Vandalismo |1|1%|1|
|Craker / Hacker |5|1%|5|
|Falsificación |9|40%|8|
|Robo de contraseñas |9|50%|8|
**5.Plan de prevención de riesgos**

A continuación  se detallan las medidas de protección que se implementaran para prevenir riesgos.

**Ambientales**

**Incendios – Inundaciones – Terremotos** 

1. Habrá que crear un documento en el cual se detalle normas y procedimientos sobre seguridad  así como asignar responsable para la actualización y comprobación del mismo .
1. Habrá que crear procedimientos detallados a seguir para los usuarios del centro en el caso de emergencia indicando responsables a personas capacitadas .
1. El centro debe contar con medidas de extinción y control .
1. Se tendrán copias de seguridad de los servidores y datos relevantes en un edificio diferente al nuestro 

**Suciedad** 

1. Se realizaran periódicamente limpiezas de los equipos aprovechando los mantenimientos .
1. Deberá de haber un registro de las limpiezas de cada equipo.
1. Deberá asignarse un responsable que se encargue de generar documentación para la correcta limpieza y impedir posibles daños en esta .

**Tecnológico** 

**Cortes del suministro eléctrico** 

1. Habrá  que  revisar  periódicamente  los  sistemas  de  alimentación  ininterrumpida  y mantenimiento en el caso de que lo necesiten .
1. Deben usarse estabilizadores de voltaje para prevenir daños en los equipos .
1. Habrá que crear un documento en el cual se detalle normas y procedimientos  así como asignar responsable para la actualización y comprobación del mismo .
1. Se deberá llevar un registro de las revisiones ,  piezas sustituidas , equipos defectuosos …

**Temperaturas muy altas o bajas** 

1. Los equipos deben estar en ubicaciones donde el ambiente sea adecuado para su correcto funcionamiento .
1. Para bajar o subir temperaturas de las maquinas podemos utilizar los aires acondicionados o las calderas .

**Averiás**

1. Los  usuarios  de  cada  equipo  deben  ser  responsables  y  mandar  una  incidencia  al administrador de los equipos.
1. Se debe realizar periódicamente mantenimiento de hardware y software actualizando los equipos 
1. Deberá generarse un registro sobre los mantenimientos así como documentación técnica de como se ha resuelto la incidencia . 

**Infecciones por código malicioso**

1. En todos los equipos debernos tener un antivirus ejecutándose siempre y en su ultima versión , castigando a aquellos que lo deshabiliten .
1. El centro es responsable de formar a los usuarios sobre los elementos de seguridad 
1. Se escanear los equipos periódicamente en busca de vulnerabilidades y se corregirán las mismas 
1. Se generaran reportes de las amenazas detectadas y la solución implantada .

**Intrusiones**

1. Implantaremos un sistema de detección de intrusos 
1. Llevaremos controles de las acciones de los equipos 
1. La información de los equipos estará cifrada 
1. Definir roles y niveles de acceso a la información

**AtaquesDDos**

1. Implantaremos firewall contra peticiones ilegitimas .
1. Tendremos un seguimiento del trafico de nuestra red periódicamente  para conocer la cantidad media de usuarios y su ubicación geográfica .
1. Valoraremos la implantación de redes de distribución de contenido o balanceadores de carga

**Ransomware**

1. Mantendremos los pc actualizados  .
1. Tendremos un antivirus que   tenga incorporado herramientas Anti Ransom.
1. No abriremos archivos o enlaces sospechosos .
1. No proporcionaremos información por teléfono .
1. Evitaremos el uso de memorias usb , si se utilizan deberán de estar cifradas .
1. Realizaremos copias de seguridad periódicamente para evitar la perdida de información en caso de sufrir el ataque .

**Humanos Hurto**

1. Se mantendrán las puertas  donde hayan equipos cerradas siempre y cuando no haya personas dentro .
1. Se tendrá un inventario de todos los equipos informáticos así como de sus periféricos .
1. Se llevara un control de entrada y salida de personas .

**Adulteración , fraude , modificación e falsificación** 

1. Solo se permitirá el acceso a la información a  personal autorizado .
1. Se harán revisiones periódicas para verificar la integridad , exactitud y validez de la misma .
1. Queda totalmente prohibido sacar información del centro .
1. En caso de que haya que transmitir información se hará de forma cifrada y solo entre personas autorizadas 
1. Se deberá comunicar cualquier anomalía a los responsables 
1. Se sancionara a las personas que se salten estas normas 
1. Se tendrán copias de seguridad de los servidores y datos relevantes en un edificio diferente al nuestro y la restauraremos en caso de perder información 

**Errores del administrador** 

1. El administrador evaluara los incidentes y se encargara de actuar en consecuencia .
1. Contara siempre con copias de seguridad tanto de la configuración como de los datos .
1. Revisara exhaustivamente los cambios o implementaciones en maquinas virtuales antes de aplicarlo a las maquinas reales .

**Revelación** 

1. La información se guardara cifrada y con contraseña para evitar que cualquiera sin autorización pueda leerla .
1. Se deberá informar al administrador en el caso de conocer la posible posesión de esta por un usuario .

**Perdida de la información** 

1. Se harán regularmente copias de la información .
1. Se configuraran los programas para guardar el progreso cada 1 minuto 
3. Se avisara inmediatamente al administrador para recuperar la información con mayor probabilidades 

**Sabotaje y Vandalismo**

1. Utilizar un antivirus que analice todas las descargas.
1. Mantener el sistema operativo y el navegador actualizados.
1. Cuidar las contraseñas y cambiarlas periódicamente.
1. No hacer clic en enlaces que resulten sospechosos.
1. Desconfiar de los correos de remitentes desconocidos.
1. No abrir ficheros adjuntos sospechosos.

**Phishing**

1. Verificaremos la fuente de los correos electrónicos , mensajes , ect.
1. No introduciremos información el las webs que accedamos a través de enlaces proveniente de los mismo 
1. Tendremos un antivirus en los equipos .
1. Revisaremos periódicamente los inicios de sesión de nuestras cuentas 
1. Pondremos en todos los sitios posibles la verificación a dos pasos 
1. Ante cualquier duda avisaremos al administrador . 

**6.Responsables de los activos** 

El centro tiene la deferencia de nombrar responsables cualificados en los siguientes ámbitos :

**-Responsable de seguridad** :con la finalidad de hacer un seguimiento y coordinar todas las iniciativas puestas en marcha por la organización en materia de Seguridad de la Información.

**-Responsable de Información:** especialmente cuando tratamos con información específica que es gestionada a través de diferentes entornos.

**-Responsables de ámbito:** en el caso de que pongamos en marcha iniciativas en el ámbito lógico, físico, legal y organizativo.

7. **Plan de contingencia** 

Un plan de contingencia detalla las medidas que se deben tomar para garantizar que una empresa pueda continuar operando en caso de alguna crisis o emergencia . 

**Ambientales**

**Incendios** 

- Si un miembro detecta fuego y sabe como utilizar los medios de extinción lo utilizara de no ser así dará la voz de alarma  .
- Si el fuego no puede ser controlado en sus comienzos se desalojara el centro .
- Los maestros llevarán a todos los estudiantes de su grupo a su área de agrupación asignada

**Inundaciones** 

- Apertura de puertas para que el agua salga, y cierre de puertas y ventanas para que el agua no entre.
- Se elevaran los dispositivos electrónicos para evitar el alcance 
- Se desalojaran las instalaciones 

**Terremotos** 

- Refugiarse debajo de un escritorio, mesa de madera u otro mueble fuerte.
- Colocarse en cuclillas o sentado, agarrado del mueble y cubriéndose la cabeza y el rostro.

**Tecnológico** 

**Cortes del suministro eléctrico** 

- Se activaran los sais y se apagaran los servidores correctamente .

**Temperaturas muy altas o bajas** 

- En el caso de que las temperaturas sean altas porque los sistemas de refrigeración no cumplan su función tendremos que prescindir temporalmente de algunos servicios para bajar las temperaturas .
- En el caso de que las temperaturas sean extremadamente bajas se encenderá la calefacción .

**Averiás**

- Sustituir los equipos afectados por unos listos para instalar .
- Se restablecerán las copias de seguridad de los afectados .
- Se destruirá los dispositivos de almacenamiento que vayan a desecharse .

**Infecciones por código malicioso**

- Se aislara el equipo .
- Se comprobara todos los medios de almacenamiento que han interactuado con el equipo y se formatearan completamente . 
- Se hará un formateo completo de los discos .
- Se restauraran las copias de seguridad .

**Intrusiones**

- Se aislara el equipo .
- Se comprobara los datos  que han interactuado con el equipo y se haran un seguimiento para comprobar su integridad .
- Se hará un formateo completo de los discos 
- Se restauraran las copias de seguridad 

**AtaquesDDos**

- Haremos un seguimiento de las peticiones y modificaremos el firewall para eliminar los países donde no es común acceder , incluso dejando solo el nuestro . 

**Ransomware**

- No pagaremos el rescate
- Se usaran medios de desencriptacion para recuperar el equipo
- En caso de no funcione el punto anterior se formateara el equipo y se restauraran las copias de seguridad 

**Humanos**

**Hurto**

- Se interpondrá  una denuncia antes los cuerpos y fuerzas  de seguridad del estado 

**Adulteración , fraude , modificación e falsificación** 

- Si el que lo produce es un alumno , se le sancionara con respecto a las normas de convivencia del centro y la decisión del profesorado .
- Si el que lo produce es un profesional del centro , se interpondrá una denuncia antes los cuerpos y fuerzas de seguridad del estado 
- Si viene de un externo , se interpondrá una denuncia antes los cuerpos y fuerzas de seguridad del estado 

**Errores del administrador** 

- Este ha de corregir lo antes posible su error . 

**Revelación** 

- Buscaremos resguardo en la legislación vigente y denunciaremos los echos  sobre dicha situación ante las autoridades policiales . 

**Perdida de la información** 

- Se utilizaran herramientas de recuperación de información .
- En caso de que no lo consigamos restauraremos las copias de seguridad 

**Sabotaje y Vandalismo**

- Se identificara al culpable y se le sancionara
- Se procurara restaurar los daños a un estado previo
- El responsable se hará cargo de los daños  económicas

**Phishing**

- Controlaremos los inicios de sesión
- Comprobaremos los registros de actividad 
- Comprobaremos los envíos realizados a través de comunicaciones 
- Cambiaremos todas las contraseñas y habilitaremos la autentificación en dos pasos 

**8.Implantación de medidas y costes** 



|**Medidas** |**Coste** |
| - | - |
|Copias de seguridad |Medio|
|Instalación de extintores|Medio|
|Elevación de dispositivos electrónicos |Bajo|
|Compra de SAIS|Medio |
|Compra de generadores eléctricos|Medio|
|Sistemas de control de clima auxiliares  |Alto |
|Destrucción de dispositivos de almacenamiento dañado |Bajo|
|Implantación redes distribuidoras de trafico|Medio|
|Implantación balanceadores de carga |Medio |
|Implantación de antivirus |Medio |
|Cifrar memorias USB |Bajo|
|Implantación controles de acceso|Alto|
|Medios de desencriptacion|Alto|
**9.Bibliografía** 

1- <https://www.incibe.es/protege-tu-empresa/que-te-interesa/plan-director-seguridad>

2- [https://www.incibe.es/protege-tu-empresa/que-te-interesa/plan-contingencia- continuidad-negocio](https://www.incibe.es/protege-tu-empresa/que-te-interesa/plan-contingencia-continuidad-negocio)

3- <https://www.incibe.es/protege-tu-empresa/herramientas/servicio-antibotnet>

4- [https://www.incibe.es/protege-tu-empresa/blog/medidas-prevencion-ataques- denegacion-servicio](https://www.incibe.es/protege-tu-empresa/blog/medidas-prevencion-ataques-denegacion-servicio)
28
