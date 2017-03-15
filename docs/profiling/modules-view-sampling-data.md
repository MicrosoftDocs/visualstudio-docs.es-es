---
title: "Vista M&#243;dulos: datos de muestreo del generador de perfiles | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Módulos (vista)"
  - "método de generación de perfiles mediante muestreo, vista Módulos"
ms.assetid: 816f5633-65d7-41e5-aee1-033628d4e2df
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Vista M&#243;dulos: datos de muestreo del generador de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vista Módulos de los datos de muestreo presenta datos de rendimiento agrupados por los módulos muestreados en los datos de generación de perfiles.  Cada módulo es la raíz de un árbol jerárquico.  Las funciones muestreadas del módulo se enumeran bajo el nodo de módulo.  
  
> [!NOTE]
>  Las características de seguridad mejoradas en Windows 8 y Windows Server 2012 requirieron cambios significativos en la forma en que el generador de perfiles de Visual Studio recopila datos en estas plataformas.  Las aplicaciones de la Tienda Windows también requieren nuevas técnicas de recolección.  Vea [Generar perfiles de aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 Si la función se estaba ejecutando cuando se recopilaron las muestras \(es decir, si la función estaba en la parte superior de la pila de llamadas\), bajo el nodo de la función se muestran las líneas de código fuente y las direcciones de instrucción que se estaban ejecutando.  Dado que los datos de una línea de código fuente o un puntero de instrucción se recopilan cuando se está ejecutando la línea o la instrucción, los valores inclusivo y exclusivo siempre son los mismos para los datos de línea y de instrucción.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Name**|Nombre del módulo, función, número de línea o dirección de puntero de instrucción.|  
|**Id. de proceso**|Identificador de proceso \(PID\) de la generación de perfiles.|  
|**Nombre del proceso**|Nombre del proceso.|  
|**Nombre de módulo**|Nombre del módulo que contiene la función, línea o puntero de instrucción.|  
|**Ruta de acceso del módulo**|Ruta de acceso del módulo que contiene la función, línea o puntero de instrucción.|  
|**Archivo de origen**|Archivo de origen que contiene la definición de esta función.|  
|**Número de línea de función**|Número de línea del inicio de esta función en el archivo de origen.|  
|**Ejemplos de inclusión**|-   En una función, el número de muestras en las que se estaba ejecutando esta función o una función llamada por esta función; es decir, el número de muestras de la pila de llamadas que contienen esta función.<br />-   En un módulo, el número de muestras en que se estaba ejecutando al menos una función del módulo.<br />-   En una línea o instrucción, el número de muestras en que se estaba ejecutando esta línea o instrucción.|  
|**Porcentaje de muestras inclusivas**|-   En una función o un módulo, el porcentaje de muestras inclusivas de esta función o módulo con respecto a todas las muestras de la ejecución de generación de perfiles.<br />-   En una línea o una instrucción, el porcentaje de tiempo de todas las muestras de la ejecución de generación de perfiles en que se estaba ejecutando esta línea o instrucción.|  
|**Ejemplos de exclusión**|-   En una función, el número de muestras de la pila de llamadas en las que se estaba ejecutando directamente esta función; es decir, el número de muestras en que esta función estaba en la parte superior de la pila de llamadas.<br />-   En un módulo, la suma de muestras exclusivas de las funciones del módulo.<br />-   En una línea o instrucción, el número de muestras en que se estaba ejecutando esta línea o instrucción.|  
|**Porcentaje de muestras exclusivas**|-   En una función o un módulo, el porcentaje de muestras exclusivas de esta función o módulo con respecto a todas las muestras de la ejecución de generación de perfiles.<br />-   En una línea o una instrucción, el porcentaje de tiempo de todas las muestras de la ejecución de generación de perfiles en que se estaba ejecutando esta línea o instrucción.|  
  
## Vea también  
 [Vista de módulos \- Muestreo](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [Vista de módulos \- Instrumentación](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Vista Módulos](../profiling/modules-view-instrumentation-data.md)