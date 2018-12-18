---
title: 'Vista Llamador y destinatario: datos de instrumentación de memoria de .NET | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Caller/Callee view
ms.assetid: da624c06-8741-4afb-aad1-f8c0002f3de2
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cf809747bff2146c6a45afd49768dbda69ae7d91
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782290"
---
# <a name="callercallee-view---net-memory-instrumentation-data"></a>Vista Llamador y destinatario: datos de instrumentación de memoria de .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La vista Llamador y destinatario de los datos de generación de perfiles de memoria de .NET recopilados mediante el método de instrumentación muestra la asignación y los datos de tiempo con relación a una función seleccionada y las funciones primarias y secundarias de esa función seleccionada. La vista Llamador y destinatario contiene tres cuadrículas.  
  
 **Función actual** se muestra en la cuadrícula central e incluye información sobre la generación de perfiles de memoria de la función seleccionada. Los valores incluyen todas las llamadas a la función que se muestrearon.  
  
 **Funciones que llamaron a la función actual** se muestra en la cuadrícula superior e incluye la cantidad del valor de la función seleccionada (actual) generado por llamadas desde la función de llamador (primaria).  
  
 **Funciones llamadas por la función actual** se muestra en la cuadrícula inferior e incluye datos de generación de perfiles de memoria para las funciones de destinatario (secundarias) de la función seleccionada cuando la función actual llamó a la función secundaria.  
  
 Haga doble clic en una fila de función de llamador o destinatario para hacer que esa fila sea la función actual.  
  
## <a name="general"></a>General  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Nombre de la función**|Nombre de la función.|  
|**Dirección de la función**|Dirección de la función.|  
|**Número de línea de la función**|Número de línea del inicio de esta función en el archivo de origen.|  
|**Número de llamadas**|Número total de llamadas realizadas a esta función.|  
|**Archivo de código fuente**|Archivo de origen que contiene la definición de esta función.|  
|**Nombre del módulo**|Nombre del módulo que contiene la función.|  
|**Ruta de acceso del módulo**|Ruta de acceso del módulo que contiene la función.|  
|**Identificador del proceso**|El identificador del proceso de la ejecución de generación de perfiles.|  
|**Nombre de proceso**|El nombre que se asigna al proceso.|  
|**Sobrecarga de tiempo exclusiva por sondeos**|Sobrecarga de tiempo para esta función debida a la instrumentación. La sobrecarga por sondeos se ha restado de todos los tiempos exclusivos.|  
|**Sobrecarga de tiempo inclusiva por sondeos**|Sobrecarga de tiempo para esta función y sus funciones secundarias debida a la instrumentación. La sobrecarga por sondeos se ha restado de todos los tiempos inclusivos.|  
|**Type**|El contexto de la función:<br /><br /> **0**: la función actual<br /><br /> **1**: una función que llama a la función actual<br /><br /> **2**: una función llamada por la función actual<br /><br /> Solo disponible en los informes de línea de comandos de [VSPerfReport](../profiling/vsperfreport.md).|  
|**Nombre de la función raíz**|El nombre de la función actual. Solo disponible en los informes de línea de comandos de [VSPerfReport](../profiling/vsperfreport.md).|  
  
## <a name="net-memory-allocation-values"></a>Valores de asignación de memoria de .NET  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Asignaciones exclusivas**|-   En la función actual, el número de objetos creados cuando la función estaba ejecutando código en el cuerpo de la función (es decir, cuando la función estaba en la parte superior de la pila de llamadas). El número no incluye los objetos creados en las funciones a las que llamó esta función.<br />-   En una función de llamador, el número de asignaciones exclusivas de la función actual generadas por llamadas de esta función de llamador.<br />-   En una función de destinatario, el número de objetos creados por las instancias de esta función a las que llamó la función actual. Este número no incluye los objetos creados por funciones a las que llamó la función de destinatario.|  
|**Porcentaje de asignaciones exclusivas**|El porcentaje de todos los objetos que se crearon durante la ejecución de la generación de perfiles que eran asignaciones exclusivas de esta función.|  
|**Asignaciones inclusivas**|-   En la función actual, el número de objetos asignados por la función en la ejecución de la generación de perfiles. El número incluye los objetos creados en las funciones de destinatario a las que llamó la función.<br />-   En una función de llamador, el número de asignaciones inclusivas de la función actual generadas por llamadas de esta función de llamador.<br />-   En una función de destinatario, el número de objetos asignados por las instancias de esta función generadas por llamadas de la función actual. El número incluye las asignaciones realizadas por funciones a las que llamó esta función de destinatario.|  
|**Porcentaje de asignaciones inclusivas**|El porcentaje de todos los objetos que se crearon durante la ejecución de la generación de perfiles que eran asignaciones inclusivas de esta función.|  
|**Bytes exclusivos**|-   En la función actual, el número de bytes de memoria asignados por la función en la ejecución de la generación de perfiles. El número no incluye la memoria asignada en las funciones de destinatario a las que llamó la función.<br />-   En una función de llamador, el número de bytes exclusivos de la función actual generados por llamadas de esta función de llamador.<br />-   En una función de destinatario, el número de bytes asignados por las instancias de esta función generadas por llamadas de la función actual. El número no incluye los bytes asignados por las funciones a las que llamó la función de destinatario.|  
|**Porcentaje de bytes exclusivos**|El porcentaje de todos los bytes de memoria que se asignaron durante la ejecución de la generación de perfiles que eran asignaciones exclusivas de esta función.|  
|**Porcentaje de bytes inclusivos**|-   En la función actual, el número de bytes en memoria asignados por la función en la ejecución de la generación de perfiles. El número incluye la memoria asignada en las funciones de destinatario a las que llamó la función.<br />-   En una función de llamador, el número de bytes inclusivos de las instancias de la función actual generadas por llamadas de esta función de llamador.<br />-   En una función de destinatario, el número de bytes asignados por las instancias de esta función generadas por llamadas de la función actual. El número incluye los bytes asignados por las funciones a las que llamó esta función de destinatario.|  
|**Porcentaje de bytes inclusivos**|El porcentaje de todos los bytes de memoria que se asignaron durante la ejecución de la generación de perfiles que eran asignaciones inclusivas de esta función.|  
  
## <a name="elapsed-inclusive-values"></a>Valores inclusivos transcurridos  
 Los valores inclusivos transcurridos indican el tiempo que una función estuvo en la pila de llamadas. Incluye el tiempo dedicado a funciones secundarias y llamadas al sistema operativo, como modificadores de contexto y operaciones de E/S.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Tiempo inclusivo transcurrido**|-   En la función actual, el tiempo dedicado a la función. El valor incluye el tiempo dedicado a funciones secundarias y llamadas al sistema operativo, como modificadores de contexto y operaciones de E/S.<br />-   En una función de llamador, la cantidad de tiempo inclusivo transcurrido de la función actual generado por llamadas de esta función de llamador.<br />-   En una función de destinatario, el tiempo dedicado a esta función generado por llamadas de la función actual. El valor incluye el tiempo dedicado a funciones secundarias y llamadas al sistema operativo, como modificadores de contexto y operaciones de E/S.|  
|**Porcentaje de tiempo inclusivo transcurrido**|El porcentaje de tiempo inclusivo transcurrido total de la ejecución de generación de perfiles que se ha empleado en el tiempo inclusivo transcurrido de esta función en este contexto.|  
|**Promedio de tiempo inclusivo transcurrido**|El promedio de tiempo inclusivo transcurrido de una llamada a esta función en este contexto.|  
|**Tiempo inclusivo transcurrido máximo**|El tiempo inclusivo transcurrido máximo de una llamada a esta función en este contexto.|  
|**Tiempo inclusivo transcurrido mínimo**|El tiempo inclusivo transcurrido mínimo de una llamada a esta función en este contexto.|  
  
## <a name="elapsed-exclusive-values"></a>Valores exclusivos transcurridos  
 Los valores exclusivos transcurridos indican el tiempo que una función se estaba ejecutando directamente en la parte superior de la pila de llamadas. Incluye el tiempo dedicado llamadas al sistema operativo, como modificadores de contexto y operaciones de E/S, pero no incluye el tiempo dedicado a funciones secundarias.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Tiempo exclusivo transcurrido**|-   En la función actual, el tiempo dedicado a la ejecución del cuerpo de la función. El valor no incluye el tiempo dedicado a funciones secundarias, pero incluye llamadas al sistema operativo, como modificadores de contexto y operaciones de E/S.<br />-   En una función de llamador, la cantidad de tiempo exclusivo transcurrido de la función actual generado por llamadas de esta función de llamador.<br />-   En una función de destinatario, el tiempo dedicado a esta función generado por llamadas de la función actual. El valor no incluye el tiempo dedicado a funciones secundarias de la función de destinatario, pero incluye las llamadas al sistema operativo, como modificadores de contexto y operaciones de E/S.|  
|**Porcentaje de tiempo exclusivo transcurrido**|El porcentaje de tiempo exclusivo transcurrido total de la ejecución de generación de perfiles que se ha empleado en el tiempo exclusivo transcurrido total de esta función en este contexto.|  
|**Promedio de tiempo exclusivo transcurrido**|El promedio de tiempo exclusivo transcurrido de una llamada a esta función en este contexto.|  
|**Tiempo exclusivo transcurrido máximo**|El tiempo exclusivo transcurrido máximo de una llamada a esta función en este contexto.|  
|**Tiempo exclusivo transcurrido mínimo**|El tiempo exclusivo transcurrido mínimo de una llamada a esta función en este contexto.|  
  
## <a name="application-inclusive-values"></a>Valores inclusivos de aplicación  
 Los valores inclusivos de aplicación indican el tiempo que una función estuvo en la pila de llamadas. No incluye el tiempo dedicado a llamadas al sistema operativo, como modificadores de contexto y operaciones de E/S, pero incluye el tiempo dedicado a funciones secundarias.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Tiempo inclusivo de aplicación**|-   En la función actual, el tiempo dedicado a la función y sus funciones secundarias. El valor no incluye el tiempo dedicado a llamadas al sistema operativo, como modificadores de contexto y operaciones de E/S.<br />-   En una función de llamador, la cantidad de tiempo inclusivo de aplicación de la función actual generado por llamadas de esta función de llamador.<br />-   En una función de destinatario, el tiempo dedicado a esta función y sus funciones secundarias generado por llamadas de la función actual. El valor no incluye el tiempo dedicado a llamadas al sistema operativo, como modificadores de contexto y operaciones de E/S.|  
|**Porcentaje de tiempo inclusivo de aplicación**|El porcentaje de tiempo inclusivo transcurrido total de la ejecución de generación de perfiles que se ha empleado en el tiempo inclusivo de aplicación total de esta función en este contexto.|  
|**Promedio de tiempo inclusivo de aplicación**|El promedio de tiempo inclusivo de aplicación de una llamada a esta función en este contexto.|  
|**Tiempo inclusivo de aplicación máximo**|El tiempo inclusivo de aplicación máximo de una llamada a esta función en este contexto.|  
|**Tiempo inclusivo de aplicación mínimo**|El tiempo inclusivo de aplicación mínimo de una llamada a esta función en este contexto.|  
  
## <a name="application-exclusive-values"></a>Valores exclusivos de aplicación  
 Los valores exclusivos de aplicación indican el tiempo dedicado a la función, excluido el tiempo dedicado a funciones secundarias. El tiempo indicado también excluye el tiempo dedicado a las llamadas al sistema operativo, como modificadores de contexto y operaciones de E/S.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Tiempo exclusivo de aplicación**|-   En la función actual, el tiempo dedicado a la ejecución del cuerpo de la función. El valor no incluye el tiempo dedicado a las funciones secundarias ni a las llamadas al sistema operativo, como modificadores de contexto y operaciones de E/S.<br />-   En una función de llamador, la cantidad de tiempo exclusivo de aplicación de la función actual generado por llamadas de esta función de llamador.<br />-   En una función de destinatario, el tiempo dedicado a esta función generado por llamadas de la función actual. El valor no incluye el tiempo dedicado a las funciones secundarias de la función de destinatario ni a las llamadas al sistema operativo, como modificadores de contexto y operaciones de E/S.|  
|**Porcentaje de tiempo exclusivo de aplicación**|El porcentaje de tiempo exclusivo transcurrido total de la ejecución de generación de perfiles que se ha empleado en el tiempo exclusivo de aplicación total de esta función en este contexto.|  
|**Promedio de tiempo exclusivo de aplicación**|El promedio de tiempo exclusivo de aplicación de una llamada a esta función en este contexto.|  
|**Tiempo exclusivo de aplicación máximo**|El tiempo exclusivo de aplicación máximo de una llamada a esta función en este contexto.|  
|**Tiempo exclusivo de aplicación mínimo**|El tiempo exclusivo de aplicación mínimo de una llamada a esta función en este contexto.|  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Personalizar las columnas de la vista de informes](../profiling/how-to-customize-report-view-columns.md)   
 [Vista Llamador y destinatario: datos de muestreo de memoria de .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Vista Llamador y destinatario: datos de instrumentación](../profiling/caller-callee-view-instrumentation-data.md)   
 [Vista Llamador y destinatario: datos de muestreo](../profiling/caller-callee-view-sampling-data.md)



