---
title: "C&#243;mo: Recopilar datos de muestreo en el nivel de l&#237;nea | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "herramientas de rendimiento, muestreo de nivel de línea"
ms.assetid: 44803aad-dd39-4c2e-9209-d35185d44983
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo: Recopilar datos de muestreo en el nivel de l&#237;nea
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El muestreo en el nivel de línea es la capacidad del generador de perfiles para determinar a qué parte del código de una función que utiliza el procesador de forma intensiva, como una función con ejemplos muy exclusivos, el procesador debe dedicar la mayor parte del tiempo.  
  
## Información general  
 Para el muestreo en el nivel de línea, el generador de perfiles recorre la pila de llamadas del programa a intervalos establecidos y agrega esos resultados.  Estos resultados muestran qué instrucciones ejecutaba el procesador cuando se tomaron los ejemplos.  A continuación, se analizan los datos recopilados sobre ejemplos exclusivos para identificar las líneas de código y el puntero de instrucciones.  
  
 El muestreo en el nivel de línea sirve tanto para el código administrado como para el nativo.  Los informes de rendimiento que muestran estos datos incluyen la vista Líneas y la vista Módulos.  
  
 La información sobre el inicio y el fin de los caracteres no está disponible para el código nativo.  Para las instrucciones multilínea, la información sobre el inicio de las líneas no está disponible para el código nativo; solo está disponible la información sobre el fin de las líneas.  
  
### Datos disponibles  
 Los datos disponibles sobre el muestreo en el nivel de línea incluyen la información siguiente:  
  
-   Nombre de la función.  
  
-   Dirección de la función.  
  
-   Inicio de línea: número de línea del código muestreado.  
  
-   Final de línea: número de la línea final del código fuente.  Generalmente coincide con los datos de "Inicio de línea", excepto cuando una sola instrucción de programa abarca varias líneas de código fuente.  
  
-   Inicio de carácter: columna inicial del ejemplo agregado.  Generalmente es 0, salvo cuando una sola línea contiene varias instrucciones de programa.  
  
-   Final de carácter: columna final del ejemplo agregado.  
  
-   IP: dirección donde se tomó el ejemplo agregado \(vista de IP únicamente\).  
  
 En la vista **Módulos**, si una función tiene estadísticas en el nivel de línea, éstas se anidan bajo cada función.  Además, se presentan las estadísticas en el nivel de IP anidadas bajo cada línea.  
  
### Desactivar el muestreo en el nivel de línea para código administrado  
 De forma predeterminada, el muestreo en el nivel de línea está activado.  Puede desactivar la recolección de datos en el nivel de línea para código administrado; para ello, siga uno de estos procedimientos:  
  
-   Antes de generar los perfiles, escriba VSPerfCLREnv \/samplelineoff.  Esto afecta a las aplicaciones y a los servicios.  
  
     O bien  
  
-   Al iniciar una aplicación, escriba VSPerfCmd \/lineoff \<otros argumentos\>.  
  
## Vea también  
 [Configurar sesiones de rendimiento](../profiling/configuring-performance-sessions.md)   
 [Analizar los datos de las Herramientas de generación de perfiles](../profiling/analyzing-performance-tools-data.md)