---
layout: single
title: ¿Como elegir un SAI?
excerpt: "Practica de seguridad informática curso 2021/2022 , en esta se desarolla un conjunto de problemas para encontrar soluciones a la hora de elegir un SAI "
date: 2021-05-22
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



**Selección SAIs Ejercicio 1**

Tenemos en nuestro CPD un conjunto de diez servidores con doble fuente redundante de 740W (carga promedio del 50 al 75% de una fuente) , dos routers cisco serie 4000 (cuyo consumo tendrás que hallar) y cuatro switches D-Link  DXS-3400 (cuyo consumo tampoco conocemos).

Deseamos garantizar la alimentación de dichos dispositivos durante un mínimo de 20 minutos mediante uno o varios SAIs enrackables (máximo 3). El tiempo máximo de recarga de los mismos será de cuatro horas. Busca tres presupuestos de SAIs de distintas marcas que cubran nuestras necesidades adecuadamente.

**Fuentes de servidores**

740w el 50 % → 370w   740w el 75 % → 555w  

La carga  media de 1 fuente de alimentación es de entre 370w a 555w .Por lo que 10 fuentes tendrán una carga de  entre 3700w a 5550w .

**Routers**

Nuestros routers son 2 modelos 4461 que cada uno consume como máximo 1000w :

![](/assets/images/seguridad/seleccionsais/Aspose.Words.569e65b1-b172-4fc6-9936-ca98e6dcf09d.001.png)

1000w el 50 % → 500w   1000w el 75 % → 750w  

La carga de estos 2 routers oscilara entre 1000w a 1500w .

**Switches**

Nuestros Switches son  4 D-Link  DXS-3400 que consume cada uno  160W :

![](/assets/images/seguridad/seleccionsais/Aspose.Words.569e65b1-b172-4fc6-9936-ca98e6dcf09d.002.png)

160w el 50 % → 80w   160w el 75 % → 120w  

La carga promedio para estos 4 Switches sera de entre 320w a 480w .

**Consumo total**

Si sumamos las cantidades que acabamos de calcular obtendremos :

- Carga total al 50% (3700 + 1000 + 320 ) = 5020w
- Carga total al 75% (5550 + 1500 + 480)  = 7530w

**Elección SAI**

Ahora buscare SAIS que para un consumo de entre 5020w a 7530w nos de mas de 20min de autonomía .

Para buscar uno necesitaremos saber cuantos VA necesitamos . Como ya conocemos el consumo de nuestros equipos haremos la conversión con la siguiente formula :

Formula : VA = W / FA

El único valor que desconocemos es el factor de potencia ,los SAI básicos tienen un Factor de potencia de 0,6 y los profesionales en torno al 0,8 – 0,9 . Así que para hacer un baremos de sais aplicaremos 0,6 y cuando tengamos seleccionados los equipos volveremos a ajustar la formula .

Tendremos que buscar sais entorno a los 8366,7 VA – 12550VA . Pero como vamos a comprar varias unidades podemos dividir los valores anteriores por la cantidad de sais que vayamos a comprar .

**Opción 1** 

3 x SAI Lampara 6000VA/6000W v1.0, on-line, doble conversión, Rack 2U+3U → [Link](https://todosai.com/sai-ups/201-SAI-Lapara-6000VA-6000W-v1-0--on-line--doble-conversion--Rack-2U3U--LA-ON-6K-RACK-8437008183978.html)

![](/assets/images/seguridad/seleccionsais/Aspose.Words.569e65b1-b172-4fc6-9936-ca98e6dcf09d.003.png)

Como vamos a tener 3 SAIs voy a dividir la potencia total  (VA) entre 3 para calcular el tiempo de uso de las baterías.  

Para ello utilizaremos esta formula ((N x V x AH x Eff ) / VA ) x 60 donde : -N = número de baterías en el SAI  ,

-V = voltaje de las baterías 

-AH=Amperios-Hora de las baterías  

-Eff = eficiencia del SAI 

-VA = Volti-Amperios del SAI 

Todos estos datos puedes sacarlo desde la ficha técnica del producto → [Link ](https://todosai.com/sai-ups/docs/Velorel/LA-ON-6-10K-RACK-V10%20-%20Hoja%20tecnica.pdf)

Para la esta opción el tiempo de duración de las baterías  es : 

Todos los equipos al 75% ((20 x 12 x 7 x 1 ) / 4125 ) x 60 = 24.4 minutos

**Opción 2** 

2 x SAI Phasak Rack 10000VA Online LCD → [Link](https://www.phasak.com/es/producto/sai-phasak-rack-10000va-online-lcd)

![](/assets/images/seguridad/seleccionsais/Aspose.Words.569e65b1-b172-4fc6-9936-ca98e6dcf09d.004.png)

El tiempo de las baterías para este sai es de : ((20 x 12 x 0 x 0.99 ) / 6125) x60 = 21 minutos 

**Opción 3** 

3 x SAI en Rack de 10.000 VA → [Link](https://www.apc.com/es/es/product/SRT10KRMXLI/smartups-srt-de-apc-10-000-va-rm-230-v/)

![](/assets/images/seguridad/seleccionsais/Aspose.Words.569e65b1-b172-4fc6-9936-ca98e6dcf09d.005.png)

El tiempo de las baterías para este sai es de : ((12 x 12 x 9 x 0.99 ) / 4183) x60 = 20,5 minutos

**Ejercicio 2** 

Explica las diferencias entre los distintos tipos de SAIs existentes (stand by, online, etc...)

**SAI Off-line o Stand-By :** Proporciona una protección básica. Protege de anomalías conocidas en redes eléctricas: fallos, subidas y bajadas de tensión. Su uso más común es en la protección de dispositivos domésticos de poca potencia como routers, ordenadores, monitores, televisores, etc. 

**SAI In-line :** Proporciona una protección intermedia solucionando  anomalías eléctricas conocidas. Respecto al SAI off-line, añade protección contra tensiones bajas o altas que se producen de forma continuada. Su uso más común es la protección de dispositivos en hogares con tensiones anómalas, pequeños comercios o empresas, ordenadores, monitores, dispositivos de red como routers y switches, cámaras de seguridad y videograbadores, etc. Dentro de los modelos interactivos existe una subgama avanzada; el SAI in-line sinusoidal. Este tipo de SAI añade una característica especialmente requerida para la protección de bombas, motores eléctricos y ordenadores con fuentes PFC activo: la alimentación de salida a través de forma de onda senoidal pura en modo batería. Los modelos que incluyen esta prestación mantendrán una alimentación a través de forma de onda senoidal pura a su salida cuando se produzca un corte de suministro y entreguen energía a través de sus baterías.

**SAI On-line:** el más sofisticado. Ofrece una protección completa contra las todas las anomalías eléctricas conocidas. Su tecnología de doble conversión garantiza el máximo nivel de protección eléctrica. Entrega una alimentación completamente ininterrumpida y a través de forma de onda senoidal pura en todo momento, lo que lo convierte en un equipo apto para trabajar, no solo conectado a una red eléctrica, sino también a generadores o grupos electrógenos. Un inconveniente es que las baterías deben sustituirse con más frecuencia, y que su coste es superior al resto de equipos de gamas más básicas. Su uso más común es en la protección de equipos de alto valor en empresas,  aplicaciones  de  tipo  industrial,  cargas  críticas,  equipos  de  uso  clínico  o  de electromedicina, etc.

**Ejercicio 3**

Deseamos comprar un SAI para trabajar con él en clase. No nos importa la potencia soportada ni la autonomía, sino las posibilidades de monitorización y configuración que ofrezca. El presupuesto máximo es de 400 euros. Estudia al menos tres posibilidades explicando el software que podríamos usar para configurarlo y monitorizarlo, ya sea software propio del SAI o una herramienta como nut.

**Opción 1**  

Salicru SPS One 1100VA V2 SAI → [Link ](https://www.pccomponentes.com/salicru-sps-one-1100va-v2-sai)

Este producto viene con un software gratuito de ges de gestión y monitorización del SAI para cierre de ficheros/aplicaciones para familia Windows, Linux y Mac; gratuito y descargable desde www.salicru.com. 

Aunque también es compatible con distintos software como :

![](/assets/images/seguridad/seleccionsais/Aspose.Words.569e65b1-b172-4fc6-9936-ca98e6dcf09d.006.png)

Desde estos software podremos realizar distintas gestiones como configurar el apagado de los equipos frente a fallos en el suministro así como monitorizar  los distintos sais de nuestra red . 

![](/assets/images/seguridad/seleccionsais/Aspose.Words.569e65b1-b172-4fc6-9936-ca98e6dcf09d.007.png)

**Opción 2**  

Salicru SPS SOHO+ 1200VA SAI→ [Link ](https://www.pccomponentes.com/salicru-sps-soho-1200va-sai)

Cuenta con interface USB con protocolo HID para el control, configuración de parámetros y cierre/hibernación del ordenador. También está disponible un paquete de softwares para la gestión y monitorización de los entornos asociados, incluso para sistemas virtualizados.

Este sai también es compatible con los programas de la primera opción .

**Opción 3**  

Riello Sentinel Pro 700VA SAI→ [Link ](https://www.pccomponentes.com/riello-sentinel-pro-700va-sai)

Este producto cuenta con su propia herramienta de monitorización que podemos descargar desde su [pagina web](https://www.riello-ups.es/products/1-sai/44-sentinel-pro) :

![](/assets/images/seguridad/seleccionsais/Aspose.Words.569e65b1-b172-4fc6-9936-ca98e6dcf09d.008.png)

Al igual que los otros software este nos permite ver el estado de nuestros sais así como configurar y parametrizar a los mismos  :

![](/assets/images/seguridad/seleccionsais/Aspose.Words.569e65b1-b172-4fc6-9936-ca98e6dcf09d.009.png)

