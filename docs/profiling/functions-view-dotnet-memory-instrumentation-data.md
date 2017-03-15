---
title: "Vista Funciones: datos de instrumentaci&#243;n de memoria .NET del generador de perfiles | Microsoft Docs"
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
  - "Funciones (vista)"
ms.assetid: cd45b379-394b-4b71-828c-92cd89e46ae0
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Vista Funciones: datos de instrumentaci&#243;n de memoria .NET del generador de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vista Funciones de datos de generación de perfiles de asignación de memoria .NET recopilados mediante el método de instrumentación muestra las funciones que asignaron memoria durante la ejecución de generación de perfiles.  Una fila de función notifica el tamaño y número de asignaciones, así como los datos de control de tiempo para la función.  
  
## General  
  
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
|**Nombre del proceso**|Nombre del proceso.|  
|**Tiempo de sobrecarga del análisis de exclusión**|La sobrecarga de tiempo para esta función causada por la instrumentación.  La sobrecarga por sondeos se ha restado de todos los tiempos exclusivos.|  
|**Tiempo de sobrecarga del análisis de inclusión**|Sobrecarga de tiempo para esta función y sus funciones secundarias debida a la instrumentación.  La sobrecarga por sondeos se ha restado de todos los tiempos inclusivos.|  
  
## Valores de memoria .NET  
 Los valores de memoria .NET inclusivos de una función indican el número \(asignaciones\) y tamaño \(bytes\) de objetos que fueron creados por la función y sus funciones secundarias.  
  
 Los valores de memoria exclusivos indican el número y tamaño de los objetos que fueron creados por la función y no por sus funciones secundarias.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Asignaciones de inclusión**|Número total de objetos creados en esta función y en las funciones a las que llamó esta función.|  
|**Porcentaje de asignaciones inclusivas**|Porcentaje de todos los objetos asignados durante la generación de perfiles que fueron objeto de asignaciones inclusivas de esta función.|  
|**Asignaciones de exclusión**|Número total de objetos creados cuando la función estaba ejecutando código en el cuerpo de la función.  Este número no incluye objetos creados en funciones a las que llamó esta función.|  
|**Porcentaje de asignaciones exclusivas**|Porcentaje de todos los objetos creados durante la generación de perfiles que fueron objeto de asignaciones exclusivas por parte de esta función.|  
|**Bytes inclusivos**|Número de bytes de memoria asignados en esta función y en funciones a las que llamó esta función.|  
|**Porcentaje de bytes inclusivos**|Porcentaje de todos los bytes de memoria asignados durante la generación de perfiles que fueron bytes inclusivos de esta función.|  
|**Bytes exclusivos**|Número de bytes de memoria asignados por esta función pero no por funciones a las que llamó esta función.|  
|**Porcentaje de bytes exclusivos**|Porcentaje de todos los bytes de memoria asignados durante la generación de perfiles que fueron bytes exclusivos de esta función.|  
  
## Valores de tiempo inclusivo transcurrido  
 Los valores de tiempo inclusivo transcurrido indican el tiempo que una función estuvo en la pila de llamadas.  El valor incluye el tiempo dedicado a funciones secundarias y llamadas al sistema operativo, como cambios de contexto y operaciones de entrada\/salida.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Tiempo de inclusión transcurrido**|El tiempo inclusivo transcurrido total de todas las llamadas a esta función.|  
|**% de tiempo inclusivo transcurrido**|Porcentaje de tiempo inclusivo transcurrido de esta función con respecto al tiempo inclusivo transcurrido total de la ejecución de generación de perfiles.|  
|**Promedio de tiempo inclusivo transcurrido**|Tiempo inclusivo transcurrido medio de una llamada a esta función.|  
|**Tiempo inclusivo máximo transcurrido**|Tiempo inclusivo transcurrido máximo de una llamada a esta función.|  
|**Tiempo inclusivo mínimo transcurrido**|Tiempo inclusivo transcurrido mínimo de una llamada a esta función.|  
  
## Valores de tiempo exclusivo transcurrido  
 Los valores de tiempo exclusivo transcurrido indican el tiempo que una función se estuvo ejecutando directamente en la parte superior de la pila de llamadas.  El valor incluye el tiempo dedicado a llamadas al sistema operativo, como cambios de contexto y operaciones de entrada\/salida, pero no incluye el tiempo dedicado a funciones secundarias.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Tiempo de exclusión transcurrido**|El tiempo exclusivo transcurrido total de todas las llamadas a esta función.|  
|**% de tiempo exclusivo transcurrido**|Porcentaje de tiempo exclusivo transcurrido total de esta función con respecto al tiempo exclusivo transcurrido total de la ejecución de generación de perfiles.|  
|**Promedio de tiempo exclusivo transcurrido**|Tiempo exclusivo transcurrido medio de una llamada a esta función.|  
|**Tiempo exclusivo máximo transcurrido**|Tiempo exclusivo transcurrido máximo de una llamada a esta función.|  
|**Tiempo exclusivo mínimo transcurrido**|Tiempo exclusivo transcurrido mínimo de una llamada a esta función.|  
  
## Valores de tiempo inclusivo de aplicación  
 Los valores de tiempo inclusivo de aplicación indican el tiempo que una función estuvo en la pila de llamadas.  El valor no incluye el tiempo dedicado a llamadas al sistema operativo como cambios de contexto y operaciones de entrada\/salida pero sí el tiempo dedicado a funciones secundarias.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Tiempo de inclusión de la aplicación**|El tiempo inclusivo de aplicación total de todas las llamadas a esta función.|  
|**% de tiempo de aplicación \(inclusive\)**|Porcentaje de tiempo inclusivo de aplicación total de esta función con respecto al tiempo inclusivo transcurrido total de la ejecución de generación de perfiles.|  
|**Promedio de tiempo inclusivo de aplicación**|Tiempo inclusivo de aplicación medio de una llamada a esta función.|  
|**Tiempo inclusivo máximo de aplicación**|Tiempo inclusivo de aplicación máximo de una llamada a esta función.|  
|**Tiempo inclusivo mínimo de aplicación**|Tiempo inclusivo de aplicación mínimo de una llamada a esta función.|  
  
## Valores de tiempo exclusivo de aplicación  
 Los valores de tiempo exclusivo de aplicación indican el tiempo que una función se estuvo ejecutando directamente en la parte superior de la pila de llamadas.  El tiempo no incluye el tiempo dedicado a llamadas al sistema operativo, como cambios de contexto y operaciones de entrada\/salida, ni incluye el tiempo dedicado a funciones secundarias.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Tiempo de exclusión de la aplicación**|El tiempo exclusivo de aplicación total de todas las llamadas a esta función.|  
|**% de tiempo de aplicación \(exclusive\)**|Porcentaje de tiempo exclusivo de aplicación total de esta función con respecto al tiempo exclusivo transcurrido total de la ejecución de generación de perfiles.|  
|**Promedio de tiempo exclusivo de aplicación**|Tiempo exclusivo de aplicación medio de una llamada a esta función.|  
|**Tiempo exclusivo máximo de aplicación**|Tiempo exclusivo de aplicación máximo de una llamada a esta función.|  
|**Tiempo exclusivo mínimo de aplicación**|Tiempo exclusivo de aplicación mínimo de una llamada a esta función.|  
  
## Vea también  
 [Cómo: Personalizar las columnas de la vista de informes](../profiling/how-to-customize-report-view-columns.md)   
 [Vista de funciones \- Muestreo](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [Vista Funciones](../profiling/functions-view-instrumentation-data.md)   
 [Vista Funciones](../profiling/functions-view-sampling-data.md)