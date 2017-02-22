---
title: "Vista L&#237;neas: datos de muestreo del generador de perfiles | Microsoft Docs"
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
ms.assetid: 46497249-c797-42c5-a02c-3e4bb3b4ee60
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Vista L&#237;neas: datos de muestreo del generador de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vista Líneas de los datos de muestreo enumera los datos de rendimiento de las instrucciones que se estaban ejecutando cuando se recopilaron las muestras en la ejecución de generación de perfiles.  
  
> [!NOTE]
>  Las características de seguridad mejoradas en Windows 8 y Windows Server 2012 requirieron cambios significativos en la forma en que el generador de perfiles de Visual Studio recopila datos en estas plataformas.  Las aplicaciones de la Tienda Windows también requieren nuevas técnicas de recolección.  Vea [Generar perfiles de aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 En un archivo de origen, una instrucción puede abarcar más de una línea y una línea puede incluir más de una instrucción.  Una instrucción se identifica por lo siguiente:  
  
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
|**Nombre de módulo**|Nombre del módulo que contiene la línea de función.|  
|**Ruta de acceso del módulo**|Ruta de acceso del módulo que contiene la línea de función.|  
|**Archivo de origen**|Archivo de origen que contiene la línea de función.|  
|**Nombre de la función**|Nombre de la función.|  
|**Número de línea de función**|Número de línea del inicio de esta función en el archivo de origen.|  
|**Dirección de función**|Dirección inicial de la función.|  
|**Comienzo de la línea de código fuente**|Número de línea inicial en el archivo de origen en el que se recolectó esta muestra.|  
|**Fin de la línea de código fuente**|Número de línea final en el archivo de origen en el que se recolectó esta muestra.|  
|**Comienzo del carácter de código fuente**|Desplazamiento del carácter inicial en la línea del archivo de origen en el que se recolectó esta muestra.|  
|**Fin del carácter de código fuente**|Desplazamiento del carácter final en la línea del archivo de origen en el que se recolectó esta muestra.|  
|**Nombre de línea**|Un identificador profiler\-generado de la línea con la sintaxis siguiente:`Source File`**;\[**`Line Number Start`**,**`Character Start`**\]\-\>;\[**`Line Number End`**,**`Character End`**\]**|  
|**Ejemplos de exclusión**|Número total de muestras recopiladas cuando se estaba ejecutando la línea de función.|  
|**Porcentaje de muestras exclusivas**|Porcentaje de todos los ejemplos de la ejecución de generación de perfiles que se recopilaron cuando se estaba ejecutando la línea de función.|  
  
## Vea también  
 [Vista de líneas \- Muestreo](../profiling/lines-view-dotnet-memory-sampling-data.md)