---
title: "Vista Llamador/Destinatario: Datos de instrumentaci&#243;n de memoria .NET del generador de perfiles | Microsoft Docs"
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
ms.assetid: da624c06-8741-4afb-aad1-f8c0002f3de2
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Vista Llamador/Destinatario: Datos de instrumentaci&#243;n de memoria .NET del generador de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vista de Llamador\/Destinatario de datos de generación de perfiles de memoria de .NET recopilados mediante el método de instrumentación muestra datos de asignación y de control de tiempo para una función seleccionada y las funciones primarias y secundarias de esa función seleccionada.  Contiene tres cuadrículas.  
  
 **Función actual** se muestra en la cuadrícula central y presenta información de generación de perfiles de memoria acerca de la función seleccionada.  Los valores incluyen todas las llamadas muestreadas a la función.  
  
 **Funciones que llamaron a la función actual** se muestra en la cuadrícula superior y presenta la cantidad del valor de la función seleccionada \(actual\) generado por llamadas de la función de llamador \(primaria\).  
  
 **Funciones llamadas por la función actual** se muestra en la cuadrícula inferior y presenta datos de generación de perfiles de memoria para las funciones de destinatario \(secundarias\) de la función seleccionada cuando la función actual llamó a la función secundaria.  
  
 Haga doble clic en una fila de función de llamador o de destinatario para convertir esa fila en la función actual.  
  
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
|**Id. de proceso**|Identificador de proceso de la generación de perfiles.|  
|**Nombre del proceso**|El nombre que se asigna al proceso.|  
|**Tiempo de sobrecarga del análisis de exclusión**|La sobrecarga de tiempo para esta función causada por la instrumentación.  La sobrecarga por sondeos se ha restado de todos los tiempos exclusivos.|  
|**Tiempo de sobrecarga del análisis de inclusión**|Sobrecarga de tiempo para esta función y sus funciones secundarias debida a la instrumentación.  La sobrecarga por sondeos se ha restado de todos los tiempos inclusivos.|  
|**Tipo**|El contexto de la función:<br /><br /> **0** \- la función actual<br /><br /> **1** \- una función que llama a la función actual<br /><br /> **2** \- una función a la que llama la función actual<br /><br /> Solo en informes de línea de comandos de [VSPerfReport](../profiling/vsperfreport.md).|  
|**Nombre de la función raíz**|El nombre de la función actual.  Solo en informes de línea de comandos de [VSPerfReport](../profiling/vsperfreport.md).|  
  
## Valores de asignación de memoria de .NET  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Asignaciones de exclusión**|-   En la función actual, el número de objetos creados cuando la función estaba ejecutando código del cuerpo de la función \(es decir, cuando la función estaba en la parte superior de la pila de llamadas\).  El número no incluye los objetos creados en funciones a las que llamó esta función.<br />-   Para una función de llamador, el número de asignaciones exclusivas de la función actual generadas por llamadas de esta función de llamador.<br />-   En una función de destinatario, el número de objetos creados por las instancias de la función a las que llamó la función actual.  Este número no incluye los objetos creados por funciones a las que llamó la función de destinatario.|  
|**Porcentaje de asignaciones exclusivas**|Porcentaje de todos los objetos creados durante la generación de perfiles que fueron objeto de asignaciones exclusivas por parte de esta función.|  
|**Asignaciones de inclusión**|-   En la función actual, número de objetos que fueron asignados por la función en la ejecución de generación de perfiles.  El número incluye los objetos creados en las funciones de destinatario a las que llamó la función.<br />-   Para una función de llamador, el número de asignaciones inclusivas de la función actual generadas por llamadas de esta función de llamador.<br />-   En una función de destinatario, el número de objetos asignados por las instancias de la función generadas por llamadas desde la función actual.  El número incluye asignaciones realizadas por funciones a las que llamó esta función de destinatario.|  
|**Porcentaje de asignaciones inclusivas**|Porcentaje de todos los objetos creados durante la generación de perfiles que fueron objeto de asignaciones inclusivas por parte de esta función.|  
|**Bytes exclusivos**|-   En la función actual, número de bytes de memoria que fueron asignados por la función en la ejecución de generación de perfiles.  El número no incluye la memoria asignada en funciones de destinatario que fueron llamadas por la función.<br />-   Para una función de llamador, el número de bytes exclusivos de la función actual generados desde llamadas realizadas por esta función de llamador.<br />-   En una función de destinatario, el número de bytes asignados por las instancias de la función generadas por llamadas desde la función actual.  El número no incluye los bytes asignados por funciones a las que llamó la función de destinatario.|  
|**Porcentaje de bytes exclusivos**|Porcentaje de todos los bytes de memoria asignados durante la generación de perfiles que fueron asignaciones exclusivas de esta función.|  
|**Bytes inclusivos**|-   En la función actual, número de bytes de memoria que fueron asignados por la función en la ejecución de generación de perfiles.  El número incluye la memoria asignada en las funciones de destinatario a las que llamó esta función.<br />-   Para una función de llamador, el número de bytes inclusivos de las instancias de la función actual generadas por llamadas de esta función de llamador.<br />-   En una función de destinatario, el número de bytes asignados por las instancias de la función generadas por llamadas desde la función actual.  El número incluye los bytes asignados por las funciones a las que llamó esta función de destinatario.|  
|**Porcentaje de bytes inclusivos**|Porcentaje de todos los bytes de memoria asignados durante la generación de perfiles que fueron asignaciones inclusivas de esta función.|  
  
## Valores de tiempo inclusivo transcurrido  
 Los valores de tiempo inclusivo transcurrido indican el tiempo que una función estuvo en la pila de llamadas.  El valor incluye el tiempo dedicado a funciones secundarias y llamadas al sistema operativo, como cambios de contexto y operaciones de entrada\/salida.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Tiempo de inclusión transcurrido**|-   En la función actual, el tiempo invertido en la función.  El valor incluye el tiempo dedicado a funciones secundarias y llamadas al sistema operativo, como cambios de contexto y operaciones de entrada\/salida.<br />-   En una función de llamador, la cantidad de tiempo inclusivo transcurrido de la función actual generado por las llamadas de esta función de llamador.<br />-   En una función de destinatario, el tiempo dedicado a esta función generado por llamadas desde la función actual.  El valor incluye el tiempo dedicado a funciones secundarias y llamadas al sistema operativo, como cambios de contexto y operaciones de entrada\/salida.|  
|**% de tiempo inclusivo transcurrido**|Porcentaje de tiempo inclusivo transcurrido de esta función en este contexto con respecto al tiempo inclusivo transcurrido total de la generación de perfiles.|  
|**Promedio de tiempo inclusivo transcurrido**|El tiempo medio inclusivo transcurrido de una llamada a esta función en este contexto.|  
|**Tiempo inclusivo máximo transcurrido**|El tiempo máximo inclusivo transcurrido de una llamada a esta función en este contexto.|  
|**Tiempo inclusivo mínimo transcurrido**|El tiempo mínimo inclusivo transcurrido de una llamada a esta función en este contexto.|  
  
## Valores de tiempo exclusivo transcurrido  
 Los valores de tiempo exclusivo transcurrido indican el tiempo que una función se estuvo ejecutando directamente en la parte superior de la pila de llamadas.  El valor incluye el tiempo dedicado a llamadas al sistema operativo, como cambios de contexto y operaciones de entrada\/salida, pero no incluye el tiempo dedicado a funciones secundarias.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Tiempo de exclusión transcurrido**|-   En la función actual, el tiempo dedicado a la ejecución del cuerpo de la función.  El valor excluye el tiempo dedicado a funciones secundarias, pero incluye las llamadas al sistema operativo, tales como cambios de contexto y operaciones de entrada\/salida.<br />-   En una función de llamador, la cantidad de tiempo exclusivo transcurrido de la función actual generado por las llamadas de esta función de llamador.<br />-   En una función de destinatario, el tiempo dedicado a esta función generado por llamadas desde la función actual.  Se excluye el tiempo dedicado a funciones secundarias de la función de destinatario, pero incluye las llamadas al sistema operativo, tales como cambios de contexto y operaciones de entrada\/salida.|  
|**% de tiempo exclusivo transcurrido**|Porcentaje de tiempo exclusivo transcurrido de esta función en este contexto con respecto al tiempo exclusivo transcurrido total de la ejecución de generación de perfiles.|  
|**Promedio de tiempo exclusivo transcurrido**|El tiempo medio exclusivo transcurrido de una llamada a esta función en este contexto.|  
|**Tiempo exclusivo máximo transcurrido**|El tiempo máximo exclusivo transcurrido de una llamada a esta función en este contexto.|  
|**Tiempo exclusivo mínimo transcurrido**|El tiempo mínimo exclusivo transcurrido de una llamada a esta función en este contexto.|  
  
## Valores de tiempo inclusivo de aplicación  
 Los valores de tiempo inclusivo de aplicación indican el tiempo que una función estuvo en la pila de llamadas.  El valor no incluye el tiempo dedicado a llamadas al sistema operativo como cambios de contexto y operaciones de entrada\/salida pero sí el tiempo dedicado a funciones secundarias.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Tiempo de inclusión de la aplicación**|-   En la función actual, el tiempo dedicado a la función y a sus funciones secundarias.  El valor excluye el tiempo dedicado a llamadas al sistema operativo, como cambios de contexto y operaciones de entrada\/salida.<br />-   En una función de llamador, la cantidad de tiempo inclusivo de aplicación de la función actual generado por las llamadas de esta función de llamador.<br />-   En una función de destinatario, el tiempo dedicado a esta función y sus funciones secundarias generadas por llamadas desde la función actual.  El valor no incluye el tiempo dedicado a llamadas al sistema operativo, como en los cambios de contexto y en las operaciones de entrada\/salida.|  
|**% de tiempo de aplicación \(inclusive\)**|Porcentaje de tiempo inclusivo de aplicación total de esta función en este contexto con respecto al tiempo inclusivo transcurrido total de la ejecución de generación de perfiles.|  
|**Promedio de tiempo inclusivo de aplicación**|El tiempo medio inclusivo de aplicación de una llamada a esta función en este contexto.|  
|**Tiempo inclusivo máximo de aplicación**|El tiempo máximo inclusivo de aplicación de una llamada a esta función en este contexto.|  
|**Tiempo inclusivo mínimo de aplicación**|El tiempo mínimo inclusivo de aplicación de una llamada a esta función en este contexto.|  
  
## Valores de tiempo exclusivo de aplicación  
 Los valores exclusivos de la aplicación indican el tiempo total invertido en la función, excepto el tiempo invertido en funciones secundarias.  El tiempo indicado también excluye el tiempo dedicado a llamadas al sistema operativo, como los cambios de contexto y las operaciones de entrada\/salida.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Tiempo de exclusión de la aplicación**|-   En la función actual, el tiempo dedicado a la ejecución del cuerpo de la función.  El valor no incluye el tiempo dedicado a funciones secundarias, ni incluye las llamadas al sistema operativo, como cambios de contexto y operaciones de entrada\/salida.<br />-   En una función de llamador, la cantidad de tiempo exclusivo de aplicación de la función actual generado por las llamadas de esta función de llamador.<br />-   En una función de destinatario, el tiempo dedicado a esta función generado por llamadas desde la función actual.  El valor no incluye el tiempo dedicado a las funciones secundarias de la función de destinatario ni las llamadas al sistema operativo, como cambios de contexto y operaciones de entrada\/salida.|  
|**% de tiempo de aplicación \(exclusive\)**|Porcentaje de tiempo exclusivo de aplicación total de esta función en este contexto con respecto al tiempo exclusivo transcurrido total de la ejecución de generación de perfiles.|  
|**Promedio de tiempo exclusivo de aplicación**|El tiempo medio exclusivo de aplicación de una llamada a esta función en este contexto.|  
|**Tiempo exclusivo máximo de aplicación**|El tiempo máximo exclusivo de aplicación de una llamada a esta función en este contexto.|  
|**Tiempo exclusivo mínimo de aplicación**|El tiempo mínimo exclusivo de aplicación de una llamada a esta función en este contexto.|  
  
## Vea también  
 [Cómo: Personalizar las columnas de la vista de informes](../profiling/how-to-customize-report-view-columns.md)   
 [Vista Llamador y destinatario \- Muestreo](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Llamador y destinatario \(Vista\)](../profiling/caller-callee-view-instrumentation-data.md)   
 [Llamador y destinatario \(Vista\)](../profiling/caller-callee-view-sampling-data.md)