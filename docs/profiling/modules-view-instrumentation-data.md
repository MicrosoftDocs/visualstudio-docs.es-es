---
title: "Vista M&#243;dulos: datos de instrumentaci&#243;n del generador de perfiles | Microsoft Docs"
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
ms.assetid: 895b9589-1987-4160-916f-53b898a69cf0
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Vista M&#243;dulos: datos de instrumentaci&#243;n del generador de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vista Módulos muestra datos de rendimiento agrupados por los módulos incluidos en los datos de generación de perfiles.  Las funciones del módulo se enumeran bajo el nodo de módulo.  
  
## General  
 Las columnas generales identifican la función en una fila de vista.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Name**|Nombre de la función o el módulo.|  
|**Número de línea de función**|Número de línea del inicio de esta función en el archivo de origen.|  
|**Número de llamadas**|Número total de llamadas realizadas a esta función o módulo.|  
|**Archivo de origen**|Archivo de origen que contiene la definición de esta función.|  
|**Nombre de módulo**|Nombre del módulo que contiene la función.|  
|**Ruta de acceso del módulo**|Ruta de acceso del módulo que contiene la función.|  
|**Id. de proceso**|Identificador de proceso \(PID\) de la generación de perfiles.|  
|**Nombre del proceso**|Nombre del proceso en el que se ejecutó el módulo o la función.|  
|**Tiempo de sobrecarga del análisis de exclusión**|Sobrecarga de tiempo para esta función o módulo causada por la instrumentación.|  
|**Tiempo de sobrecarga del análisis de inclusión**|Sobrecarga de tiempo para esta función o módulo y sus funciones secundarias causada por la instrumentación.|  
  
## Valores de tiempo inclusivo transcurrido  
 Los valores de tiempo inclusivo transcurrido indican el tiempo que una función estuvo en la pila de llamadas.  El valor incluye el tiempo dedicado a funciones secundarias y llamadas al sistema operativo, como cambios de contexto y operaciones de entrada\/salida.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Tiempo de inclusión transcurrido**|-   En una función, el tiempo invertido en dicha función.  Esto incluye el tiempo dedicado a las funciones secundarias y llamadas al sistema operativo, como cambios de contexto y operaciones de entrada\/salida.<br />-   En un módulo, el tiempo durante el que al menos una función del módulo estuvo en la pila de llamadas.|  
|**% de tiempo inclusivo transcurrido**|Porcentaje de tiempo inclusivo transcurrido total de este módulo o función con respecto al tiempo inclusivo transcurrido total de la generación de perfiles.|  
|**Promedio de tiempo inclusivo transcurrido**|-   En una función, el tiempo medio inclusivo transcurrido de una llamada a esta función.<br />-   En un módulo, el tiempo medio inclusivo transcurrido de todas las llamadas a las funciones del módulo.|  
|**Tiempo inclusivo máximo transcurrido**|-   En una función, el tiempo máximo inclusivo transcurrido de una llamada a esta función.<br />-   En un módulo, el tiempo máximo inclusivo transcurrido de todas las llamadas a las funciones del módulo.|  
|**Tiempo inclusivo mínimo transcurrido**|-   En una función, el tiempo mínimo inclusivo transcurrido de una llamada a este módulo o función.<br />-   En un módulo, el tiempo mínimo inclusivo transcurrido de todas las llamadas a las funciones del módulo.|  
  
## Valores de tiempo exclusivo transcurrido  
 Los valores de tiempo exclusivo transcurrido indican el tiempo que una función se estuvo ejecutando directamente en la parte superior de la pila de llamadas.  El valor incluye el tiempo dedicado a llamadas al sistema operativo, como cambios de contexto y operaciones de entrada\/salida, pero no el tiempo dedicado a funciones secundarias.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Tiempo de exclusión transcurrido**|-   En una función, el tiempo invertido en el módulo o la función.  Esto incluye las llamadas al sistema operativo, tales como cambios de contexto y operaciones de entrada\/salida, pero excluye el tiempo dedicado a las funciones secundarias.<br />-   En un módulo, la suma de los tiempos exclusivos transcurridos de las funciones del módulo.|  
|**% de tiempo exclusivo transcurrido**|Porcentaje de tiempo exclusivo transcurrido total de este módulo o función con respecto al tiempo exclusivo transcurrido total de la generación de perfiles.|  
|**Promedio de tiempo exclusivo transcurrido**|-   En una función, el tiempo medio exclusivo transcurrido de una llamada a esta función.<br />-   En un módulo, el tiempo medio exclusivo transcurrido de todas las llamadas a las funciones del módulo.|  
|**Tiempo exclusivo máximo transcurrido**|-   En una función, el tiempo máximo exclusivo transcurrido de una llamada a esta función.<br />-   En un módulo, el tiempo máximo exclusivo transcurrido de todas las llamadas a las funciones del módulo.|  
|**Tiempo exclusivo mínimo transcurrido**|-   En una función, el tiempo mínimo exclusivo transcurrido de una llamada a este módulo o función.<br />-   En un módulo, el tiempo mínimo exclusivo transcurrido de todas las llamadas a las funciones del módulo.|  
  
## Valores de tiempo inclusivo de aplicación  
 Los valores de tiempo inclusivo de aplicación indican el tiempo que una función estuvo en la pila de llamadas.  El valor no incluye el tiempo dedicado a las llamadas al sistema operativo, como cambios de contexto y operaciones de entrada\/salida. Sin embargo, el valor sí incluye el tiempo dedicado a las funciones secundarias.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Tiempo de inclusión de la aplicación**|-   En una función, el tiempo invertido en las llamadas a la función.  Esto incluye el tiempo dedicado a las funciones secundarias, pero excluye las llamadas al sistema operativo, tales como cambios de contexto y operaciones de entrada\/salida.<br />-   En un módulo, el tiempo durante el que al menos una función del módulo estuvo en la pila de llamadas.  Esto excluye el tiempo dedicado a las llamadas al sistema operativo.|  
|**% de tiempo de aplicación \(inclusive\)**|Porcentaje de tiempo inclusivo de aplicación de este módulo o función con respecto al tiempo inclusivo transcurrido total de la generación de perfiles.|  
|**Promedio de tiempo inclusivo de aplicación**|-   En una función, el tiempo medio inclusivo de aplicación de una llamada a esta función.<br />-   En un módulo, el tiempo medio inclusivo de aplicación de todas las llamadas a las funciones del módulo.|  
|**Tiempo inclusivo máximo de aplicación**|-   En una función, el tiempo máximo inclusivo de aplicación de una llamada a esta función.<br />-   En un módulo, el tiempo máximo inclusivo de aplicación de todas las llamadas a las funciones del módulo.|  
|**Tiempo inclusivo mínimo de aplicación**|-   En una función, el tiempo mínimo inclusivo de aplicación de una llamada a este módulo o función.<br />-   En un módulo, el tiempo mínimo inclusivo de aplicación de todas las llamadas a las funciones del módulo.|  
  
## Valores de tiempo exclusivo de aplicación  
 Los valores exclusivos de la aplicación indican el tiempo invertido en el módulo o la función.  Esto excluye el tiempo dedicado a funciones secundarias, y también excluye las llamadas al sistema operativo, como cambios de contexto y operaciones de entrada\/salida.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Tiempo de exclusión de la aplicación**|El tiempo exclusivo de aplicación total de todas las llamadas a este módulo o función.|  
|**% de tiempo de aplicación \(exclusive\)**|Porcentaje de tiempo exclusivo de aplicación de este módulo o función con respecto al tiempo exclusivo transcurrido total de la generación de perfiles.|  
|**Promedio de tiempo exclusivo de aplicación**|-   En una función, el tiempo medio exclusivo de aplicación de una llamada a esta función.<br />-   En un módulo, el tiempo medio exclusivo de aplicación de todas las llamadas a las funciones del módulo.|  
|**Tiempo exclusivo máximo de aplicación**|-   En una función, el tiempo máximo exclusivo de aplicación de una llamada a esta función.<br />-   En un módulo, el tiempo máximo exclusivo de aplicación de todas las llamadas a las funciones del módulo.|  
|**Tiempo exclusivo mínimo de aplicación**|-   En una función, el tiempo mínimo exclusivo de aplicación de una llamada a este módulo o función.<br />-   En un módulo, el tiempo mínimo exclusivo de aplicación de todas las llamadas a las funciones del módulo.|  
  
## Vea también  
 [Vista Módulos](../profiling/modules-view-sampling-data.md)   
 [Vista de módulos \- Instrumentación](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Vista de módulos \- Muestreo](../profiling/modules-view-dotnet-memory-sampling-data.md)