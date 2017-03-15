---
title: "Vista &#193;rbol de llamadas: datos de instrumentaci&#243;n del generador de perfiles | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Árbol de llamadas (vista)"
ms.assetid: 306bd176-0ce9-4a10-89ca-20b043d37d4e
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Vista &#193;rbol de llamadas: datos de instrumentaci&#243;n del generador de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Los valores de una función del árbol de llamadas indican el tiempo dedicado a las instancias de la función llamadas por la función primaria en el árbol de llamadas.  Los valores de porcentaje se calculan mediante la comparación del valor de las instancias de la función con el tiempo inclusivo transcurrido total de todas las funciones de la ejecución de generación de perfiles.  
  
## General  
 Las columnas generales identifican la función en una fila de vista.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Nombre de la función**|Nombre de la función.|  
|**Dirección de función**|Dirección de la función.|  
|**Número de línea de función**|Número de línea del inicio de esta función en el archivo de origen.|  
|**Número de llamadas**|Número total de llamadas realizadas a esta función.|  
|**Archivo de origen**|Archivo de origen que contiene la definición de esta función.|  
|**Nombre de módulo**|Nombre del módulo que contiene la función.|  
|**Ruta de acceso del módulo**|Ruta de acceso del módulo que contiene la función.|  
|**Id. de proceso**|Identificador de proceso \(PID\) de la generación de perfiles.|  
|**Nombre del proceso**|El nombre que se asigna al proceso.|  
|**Tiempo de sobrecarga del análisis de exclusión**|Sobrecarga de tiempo para esta función debida a la instrumentación.  La sobrecarga por sondeos se ha restado de todos los tiempos exclusivos.|  
|**Tiempo de sobrecarga del análisis de inclusión**|Sobrecarga de tiempo para esta función y sus funciones secundarias debida a la instrumentación.  La sobrecarga por sondeos se ha restado de todos los tiempos inclusivos.|  
|**Nivel**|Profundidad de la función en el árbol de llamadas.  Solo en informes de línea de comandos de [VSPerfReport](../profiling/vsperfreport.md).|  
  
## Valores de tiempo inclusivo transcurrido  
 Los valores de tiempo inclusivo transcurrido indican el tiempo en la pila de llamadas de las instancias de la función llamadas por la función primaria en el árbol de llamadas.  El valor incluye el tiempo dedicado a las funciones secundarias llamadas por la función y a las llamadas al sistema operativo, como cambios de contexto y operaciones de entrada\/salida.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Tiempo de inclusión transcurrido**|El tiempo inclusivo transcurrido total de todas las llamadas a esta función en este contexto.|  
|**% de tiempo inclusivo transcurrido**|Porcentaje de tiempo inclusivo transcurrido de esta función en este contexto con respecto al tiempo inclusivo transcurrido total de la ejecución de generación de perfiles.|  
|**Promedio de tiempo inclusivo transcurrido**|El tiempo medio inclusivo transcurrido de una llamada a esta función en este contexto.|  
|**Tiempo inclusivo máximo transcurrido**|El tiempo máximo inclusivo transcurrido de una llamada a esta función en este contexto.|  
|**Tiempo inclusivo mínimo transcurrido**|El tiempo mínimo inclusivo transcurrido de una llamada a esta función en este contexto.|  
  
## Valores de tiempo exclusivo transcurrido  
 Los valores de tiempo exclusivo transcurrido indican el tiempo que las instancias de una función a las que llamó la función primaria del árbol de llamadas estuvieron ejecutando código del cuerpo de la función; es decir, el tiempo en que la función estuvo en la parte superior de la pila de llamadas.  El tiempo incluye el tiempo de las llamadas al sistema operativo, como en los cambios de contexto y en las operaciones de entrada\/salida.  Sin embargo, el tiempo no incluye el tiempo total invertido en las funciones secundarias llamadas por la función.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Tiempo de exclusión transcurrido**|El tiempo exclusivo transcurrido total de todas las llamadas a esta función en este contexto.|  
|**% de tiempo exclusivo transcurrido**|Porcentaje de tiempo exclusivo transcurrido de esta función en este contexto con respecto al tiempo exclusivo transcurrido total de la ejecución de generación de perfiles.|  
|**Promedio de tiempo exclusivo transcurrido**|El tiempo medio exclusivo transcurrido de una llamada a esta función en este contexto.|  
|**Tiempo exclusivo máximo transcurrido**|El tiempo máximo exclusivo transcurrido de una llamada a esta función en este contexto.|  
|**Tiempo exclusivo mínimo transcurrido**|El tiempo mínimo exclusivo transcurrido de una llamada a esta función en este contexto.|  
  
## Valores de tiempo inclusivo de aplicación  
 Los valores de tiempo inclusivo de aplicación indican el tiempo en la pila de llamadas de las instancias de una función llamadas por la función primaria en el árbol de llamadas.  El valor no incluye el tiempo dedicado a las llamadas al sistema operativo, como cambios de contexto y operaciones de entrada\/salida. Sin embargo, el valor sí incluye el tiempo dedicado a las funciones secundarias llamadas por esta función.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Tiempo de inclusión de la aplicación**|El tiempo inclusivo de aplicación total de todas las llamadas a esta función en este contexto.|  
|**% de tiempo de aplicación \(inclusive\)**|Porcentaje de tiempo inclusivo de aplicación total de esta función en este contexto con respecto al tiempo inclusivo transcurrido total de la ejecución de generación de perfiles.|  
|**Promedio de tiempo inclusivo de aplicación**|El tiempo medio inclusivo de aplicación de una llamada a esta función en este contexto.|  
|**Tiempo inclusivo máximo de aplicación**|El tiempo máximo inclusivo de aplicación de una llamada a esta función en este contexto.|  
|**Tiempo inclusivo mínimo de aplicación**|El tiempo mínimo inclusivo de aplicación de una llamada a esta función en este contexto.|  
  
## Valores de tiempo exclusivo de aplicación  
 Los valores de tiempo exclusivo de aplicación indican el tiempo que las instancias de una función a las que llamó la función primaria del árbol de llamadas estuvieron directamente ejecutando código del cuerpo de la función; es decir, el tiempo en que la función estuvo en la parte superior de la pila de llamadas.  El valor no incluye el tiempo dedicado a llamadas al sistema operativo, como en los cambios de contexto y en las operaciones de entrada\/salida.  Tampoco incluye el tiempo total invertido en las funciones secundarias llamadas por la función.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Tiempo de exclusión de la aplicación**|El tiempo exclusivo de aplicación total de todas las llamadas a esta función en este contexto.|  
|**% de tiempo de aplicación \(exclusive\)**|Porcentaje de tiempo exclusivo de aplicación total de esta función en este contexto con respecto al tiempo exclusivo transcurrido total de la ejecución de generación de perfiles.|  
|**Promedio de tiempo exclusivo de aplicación**|El tiempo medio exclusivo de aplicación de una llamada a esta función en este contexto.|  
|**Tiempo exclusivo máximo de aplicación**|El tiempo máximo exclusivo de aplicación de una llamada a esta función en este contexto.|  
|**Tiempo exclusivo mínimo de aplicación**|El tiempo mínimo exclusivo de aplicación de una llamada a esta función en este contexto.|  
  
## Vea también  
 [Cómo: Personalizar las columnas de la vista de informes](../profiling/how-to-customize-report-view-columns.md)   
 [Vista Árbol de llamadas](../profiling/call-tree-view-sampling-data.md)   
 [Vista Árbol de llamadas \- Instrumentación](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Vista Árbol de llamadas \- Muestreo](../profiling/call-tree-view-dotnet-memory-sampling-data.md)