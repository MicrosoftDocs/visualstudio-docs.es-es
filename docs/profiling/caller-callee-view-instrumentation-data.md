---
title: "Vista Llamador y destinatario: datos de instrumentaci&#243;n del generador de perfiles | Microsoft Docs"
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
  - "Llamador y destinatario (vista)"
ms.assetid: 0908d354-aa5c-4518-8631-e25b8e7649e5
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Vista Llamador y destinatario: datos de instrumentaci&#243;n del generador de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vista Llamador y destinatario muestra información de generación de perfiles acerca de una función seleccionada y sus funciones primarias y secundarias en el árbol de llamadas.  Contiene tres cuadrículas.  
  
 **Función actual** se muestra en la cuadrícula central y presenta información de generación de perfiles acerca de la función seleccionada.  Los valores incluyen todas las llamadas a la función.  
  
 **Funciones que llamaron a la función actual** se muestra en la cuadrícula superior y presenta información de generación de perfiles acerca de las funciones de llamador \(primarias\) de la función seleccionada.  Los valores indican la cantidad de valores de la función actual que fueron generados por las llamadas de esta función de llamador.  
  
 **Funciones llamadas por la función actual** se muestra en la cuadrícula inferior y presenta información de generación de perfiles acerca de las instancias de las funciones destinatarias \(secundarias\) de la función seleccionada.  Los valores indican solamente el tiempo invertido en la función secundaria cuando la llamó la función actual.  
  
## General  
 Las columnas generales identifican la función en una fila de vista.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Nombre de la función**|Nombre de la función.|  
|**Dirección de función**|Dirección de la función.|  
|**Número de línea de función**|Número de línea del inicio de esta función en el archivo de origen.|  
|**Número de llamadas**|Número total de llamadas realizadas a la función.|  
|**Archivo de origen**|Archivo de origen que contiene la definición de esta función.|  
|**Nombre de módulo**|Nombre del módulo que contiene la función.|  
|**Ruta de acceso del módulo**|Ruta de acceso del módulo que contiene la función.|  
|**Id. de proceso**|Identificador de proceso \(PID\) de la generación de perfiles.|  
|**Nombre del proceso**|Nombre del proceso.|  
|**Tiempo de sobrecarga del análisis de exclusión**|Sobrecarga de tiempo para esta función debida a la instrumentación.  La sobrecarga por sondeos se ha restado de todos los tiempos exclusivos.|  
|**Tiempo de sobrecarga del análisis de inclusión**|Sobrecarga de tiempo para esta función y sus funciones secundarias debida a la instrumentación.  La sobrecarga por sondeos se ha restado de todos los tiempos inclusivos.|  
|**Tipo**|El contexto de la función:<br /><br /> **0** \- la función actual<br /><br /> **1** \- una función que llama a la función actual<br /><br /> **2** \- una función a la que llama la función actual<br /><br /> Solo en informes de línea de comandos de [VSPerfReport](../profiling/vsperfreport.md).|  
|**Nombre de la función raíz**|El nombre de la función actual.  Solo en informes de línea de comandos de [VSPerfReport](../profiling/vsperfreport.md).|  
  
## Valores de tiempo inclusivo transcurrido  
 Los valores de tiempo inclusivo transcurrido indican el tiempo que una función estuvo en la pila de llamadas.  Se incluye el tiempo dedicado a funciones secundarias y a llamadas al sistema operativo, como cambios de contexto y operaciones de entrada\/salida.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Tiempo de inclusión transcurrido**|-   En la función actual, el tiempo invertido en la función.  El valor incluye el tiempo dedicado a funciones secundarias y llamadas al sistema operativo, como cambios de contexto y operaciones de entrada\/salida.<br />-   En una función de llamador, la cantidad de tiempo inclusivo transcurrido de la función actual generado por las llamadas de esta función de llamador.<br />-   En una función de destinatario, el tiempo dedicado a instancias de la función generadas por llamadas desde la función actual.  Se incluye el tiempo dedicado a funciones secundarias del destinatario y a llamadas al sistema operativo, como cambios de contexto y operaciones de entrada\/salida.|  
|**% de tiempo inclusivo transcurrido**|Porcentaje de tiempo inclusivo transcurrido de esta función en este contexto con respecto al tiempo inclusivo transcurrido total de la generación de perfiles.|  
|**Promedio de tiempo inclusivo transcurrido**|El tiempo medio inclusivo transcurrido de una llamada a esta función en este contexto.|  
|**Tiempo inclusivo máximo transcurrido**|El tiempo máximo inclusivo transcurrido de una llamada a esta función en este contexto.|  
|**Tiempo inclusivo mínimo transcurrido**|El tiempo mínimo inclusivo transcurrido de una llamada a esta función en este contexto.|  
  
## Valores de tiempo exclusivo transcurrido  
 Los valores de tiempo exclusivo transcurrido indican el tiempo que una función se estuvo ejecutando directamente en la parte superior de la pila de llamadas.  El valor incluye el tiempo dedicado a llamadas al sistema operativo, como cambios de contexto y operaciones de entrada\/salida, pero no el tiempo dedicado a funciones secundarias.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Tiempo de exclusión transcurrido**|-   En la función actual, el tiempo dedicado a la ejecución directa de la función.  El valor incluye el tiempo dedicado a funciones secundarias y llamadas al sistema operativo, como cambios de contexto y operaciones de entrada\/salida.<br />-   En una función de llamador, la cantidad de tiempo exclusivo transcurrido de la función actual generado por las llamadas de esta función de llamador.<br />-   En una función de destinatario, el tiempo dedicado a instancias de la función generadas por llamadas desde la función actual.  Se excluye el tiempo dedicado a funciones secundarias de la función de destinatario, pero se incluyen las llamadas al sistema operativo, tales como cambios de contexto y operaciones de entrada\/salida.|  
|**% de tiempo exclusivo transcurrido**|Porcentaje de tiempo exclusivo transcurrido de esta función en este contexto con respecto al tiempo exclusivo transcurrido total de la ejecución de generación de perfiles.|  
|**Promedio de tiempo exclusivo transcurrido**|El tiempo medio exclusivo transcurrido de una llamada a esta función en este contexto.|  
|**Tiempo exclusivo máximo transcurrido**|El tiempo máximo exclusivo transcurrido de una llamada a esta función en este contexto.|  
|**Tiempo exclusivo mínimo transcurrido**|El tiempo mínimo exclusivo transcurrido de una llamada a esta función en este contexto.|  
  
## Valores de tiempo inclusivo de aplicación  
 Los valores de tiempo inclusivo de aplicación indican el tiempo que una función estuvo en la pila de llamadas.  El valor no incluye el tiempo dedicado a llamadas al sistema operativo como cambios de contexto y operaciones de entrada\/salida pero sí el tiempo dedicado a funciones secundarias.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Tiempo de inclusión de la aplicación**|-   En la función actual, el tiempo dedicado a la función y a sus funciones secundarias.  El valor excluye el tiempo dedicado a llamadas al sistema operativo, como cambios de contexto y operaciones de entrada\/salida.<br />-   En una función de llamador, la cantidad de tiempo inclusivo de aplicación de la función actual generado por las llamadas de esta función de llamador.<br />-   En una función de destinatario, el tiempo dedicado a instancias de la función generadas por llamadas desde la función actual.  El valor incluye el tiempo dedicado a las funciones secundarias de la función de destinatario, pero no el dedicado a las llamadas al sistema operativo, como cambios de contexto y operaciones de entrada\/salida.|  
|**% de tiempo de aplicación \(inclusive\)**|Porcentaje de tiempo inclusivo de aplicación total de esta función en este contexto con respecto al tiempo inclusivo transcurrido total de la ejecución de generación de perfiles.|  
|**Promedio de tiempo inclusivo de aplicación**|El tiempo medio inclusivo de aplicación de una llamada a esta función en este contexto.|  
|**Tiempo inclusivo máximo de aplicación**|El tiempo máximo inclusivo de aplicación de una llamada a esta función en este contexto.|  
|**Tiempo inclusivo mínimo de aplicación**|El tiempo mínimo inclusivo de aplicación de una llamada a esta función en este contexto.|  
  
## Valores de tiempo exclusivo de aplicación  
 Los valores exclusivos de la aplicación indican el tiempo invertido en la función.  Esto excluye el tiempo dedicado a funciones secundarias, y también excluye las llamadas al sistema operativo, como cambios de contexto y operaciones de entrada\/salida.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Tiempo de exclusión de la aplicación**|-   En la función actual, el tiempo dedicado a la ejecución directa de la función.  El valor no incluye el tiempo dedicado a funciones secundarias, ni incluye las llamadas al sistema operativo, como cambios de contexto y operaciones de entrada\/salida.<br />-   En una función de llamador, la cantidad de tiempo exclusivo de aplicación de la función actual generado por las llamadas de esta función de llamador.<br />-   En una función de destinatario, el tiempo dedicado a instancias de la función generadas por llamadas desde la función actual.  El valor no incluye el tiempo dedicado a las funciones secundarias de la función de destinatario ni las llamadas al sistema operativo, como cambios de contexto y operaciones de entrada\/salida.|  
|**% de tiempo de aplicación \(exclusive\)**|Porcentaje de tiempo exclusivo de aplicación total de esta función en este contexto con respecto al tiempo exclusivo transcurrido total de la ejecución de generación de perfiles.|  
|**Promedio de tiempo exclusivo de aplicación**|El tiempo medio exclusivo de aplicación de una llamada a esta función en este contexto.|  
|**Tiempo exclusivo máximo de aplicación**|El tiempo máximo exclusivo de aplicación de una llamada a esta función en este contexto.|  
|**Tiempo exclusivo mínimo de aplicación**|El tiempo mínimo exclusivo de aplicación de una llamada a esta función en este contexto.|  
  
## Vea también  
 [Cómo: Personalizar las columnas de la vista de informes](../profiling/how-to-customize-report-view-columns.md)   
 [Llamador y destinatario \(Vista\)](../profiling/caller-callee-view-sampling-data.md)   
 [Vista Llamador y destinatario \- Muestreo](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Vista Llamador y destinatario \- Instrumentación](../profiling/caller-callee-view-net-memory-instrumentation-data.md)