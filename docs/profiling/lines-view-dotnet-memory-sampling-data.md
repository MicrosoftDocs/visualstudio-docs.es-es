---
title: "Vista L&#237;neas: datos de muestreo de memoria de .NET del generador de perfiles | Microsoft Docs"
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
  - "Líneas (vista)"
ms.assetid: 6631ab87-0e62-4c76-a063-4ea7222b07da
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Vista L&#237;neas: datos de muestreo de memoria de .NET del generador de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vista Líneas de datos de generación de perfiles de asignación de memoria .NET que utiliza el método de muestreo muestra las instrucciones que asignaron memoria durante la ejecución de generación de perfiles.  Las columnas también incluyen el tamaño y número de asignaciones.  
  
 En un archivo de origen, una instrucción puede abarcar más de una línea y una línea puede incluir más de una instrucción.  
  
 Una instrucción se identifica por lo siguiente:  
  
-   El archivo de origen que contiene la instrucción de la función.  
  
-   La función que contiene la instrucción.  
  
-   La línea de código fuente en que se inicia la instrucción.  
  
-   El carácter de la línea de código fuente en que se inicia la instrucción.  
  
-   La línea de código fuente en que finaliza la instrucción.  
  
-   El carácter de la línea de origen en que finaliza la instrucción.  
  
 La columna Nombre de línea proporciona una concatenación ordenable de datos del identificador.  
  
 Por definición, una instrucción no llama a otras funciones.  Por tanto, solamente se enumeran los valores exclusivos.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Id. de proceso**|Identificador de proceso \(PID\) de la generación de perfiles.|  
|**Nombre del proceso**|Nombre del proceso.|  
|**Nombre de módulo**|Nombre del módulo que contiene la instrucción.|  
|**Ruta de acceso del módulo**|Ruta de acceso del módulo que contiene la instrucción.|  
|**Archivo de origen**|Archivo de origen que contiene la instrucción.|  
|**Nombre de la función**|Nombre de la función que contiene la instrucción.|  
|**Número de línea de función**|Número de línea del inicio de esta función en el archivo de origen.|  
|**Dirección de función**|Dirección inicial de la función.|  
|**Comienzo de la línea de código fuente**|Número de línea inicial en el archivo de origen donde se produjo la asignación.|  
|**Fin de la línea de código fuente**|Número de línea final en el archivo de origen donde se produjo la asignación.|  
|**Comienzo del carácter de código fuente**|Desplazamiento del carácter inicial en la línea del archivo de origen donde se produjo la asignación.|  
|**Fin del carácter de código fuente**|Desplazamiento del carácter final en la línea del archivo de origen donde se produjo la asignación.|  
|**Nombre de línea**|Un identificador profiler\-generado de la línea con la sintaxis siguiente:`Source File`**;\[**`Line Number Start`**,**`Character Start`**\]\-\>;\[**`Line Number Start,Character Start`**\]**|  
|**Asignaciones de exclusión**|El número total de objetos que se crearon en esta línea.|  
|**Porcentaje de asignaciones exclusivas**|Porcentaje de todos los objetos creados durante la generación de perfiles que fueron asignados por esta línea.|  
|**Bytes exclusivos**|Porcentaje de bytes asignados en esta línea con respecto a todos los bytes de memoria asignados durante la ejecución de generación de perfiles.|  
|**Porcentaje de bytes exclusivos**|Porcentaje de bytes asignados en esta línea con respecto a todos los bytes de memoria asignados durante la ejecución de generación de perfiles.|  
  
## Vea también  
 [Vista Líneas](../profiling/lines-view-sampling-data.md)