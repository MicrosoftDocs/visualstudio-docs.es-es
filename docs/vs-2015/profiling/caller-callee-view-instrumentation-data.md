---
title: 'Vista llamador y destinatario: datos de instrumentación | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Caller/Callee view
ms.assetid: 0908d354-aa5c-4518-8631-e25b8e7649e5
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3c8db1d559682ccb0f202d100fac6a586d3477cd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68147918"
---
# <a name="callercallee-view---instrumentation-data"></a>Vista llamador y destinatario: datos de instrumentación
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La vista Llamador y destinatario muestra información de generación de perfiles sobre una función seleccionada y sus funciones primarias y secundarias en el árbol de llamadas. La vista Llamador y destinatario contiene tres cuadrículas.  
  
 **Función actual** se muestra en la cuadrícula central e incluye información sobre la generación de perfiles de la función seleccionada. Los valores incluyen todas las llamadas a la función.  
  
 **Funciones que llamaron a la función actual** se muestra en la cuadrícula superior e incluye información de generación de perfiles sobre las funciones de llamador (primaria) de la función seleccionada. Los valores indican la cantidad del valor de la función actual generado por las llamadas de esta función de llamador.  
  
 **Funciones llamadas por la función actual** se muestra en la cuadrícula inferior e incluye información de generación de perfiles sobre las instancias de las funciones de destinatario (secundarias) de la función seleccionada. Los valores indican solo el tiempo dedicado a la función secundaria cuando la llamó la función actual.  
  
## <a name="general"></a>General  
 En las columnas generales se identifica la función en una fila de la vista.  
  
|Columna|DESCRIPCIÓN|  
|------------|-----------------|  
|**Nombre de la función**|Nombre de la función.|  
|**Dirección de la función**|Dirección de la función.|  
|**Número de línea de la función**|Número de línea del inicio de esta función en el archivo de origen.|  
|**Número de llamadas**|El número total de llamadas realizadas a esta función.|  
|**Archivo de código fuente**|Archivo de origen que contiene la definición de esta función.|  
|**Nombre del módulo**|Nombre del módulo que contiene la función.|  
|**Ruta de acceso del módulo**|Ruta de acceso del módulo que contiene la función.|  
|**Identificador del proceso**|Identificador de proceso (PID) de la ejecución de generación de perfiles.|  
|**Nombre de proceso**|Nombre del proceso.|  
|**Sobrecarga de tiempo exclusiva por sondeos**|Sobrecarga de tiempo para esta función debida a la instrumentación. La sobrecarga por sondeos se ha restado de todos los tiempos exclusivos.|  
|**Sobrecarga de tiempo inclusiva por sondeos**|Sobrecarga de tiempo para esta función y sus funciones secundarias debida a la instrumentación. La sobrecarga por sondeos se ha restado de todos los tiempos inclusivos.|  
|**Type**|El contexto de la función:<br /><br /> **0**: la función actual<br /><br /> **1**: una función que llama a la función actual<br /><br /> **2**: una función llamada por la función actual<br /><br /> Solo disponible en los informes de línea de comandos de [VSPerfReport](../profiling/vsperfreport.md).|  
|**Nombre de la función raíz**|El nombre de la función actual. Solo disponible en los informes de línea de comandos de [VSPerfReport](../profiling/vsperfreport.md).|  
  
## <a name="elapsed-inclusive-values"></a>Valores inclusivos transcurridos  
 Los valores inclusivos transcurridos indican el tiempo que una función estuvo en la pila de llamadas. Incluye el tiempo dedicado a funciones secundarias y llamadas al sistema operativo, como modificadores de contexto y operaciones de E/S.  
  
|Columna|DESCRIPCIÓN|  
|------------|-----------------|  
|**Tiempo inclusivo transcurrido**|-   En la función actual, el tiempo dedicado a la función. El valor incluye el tiempo dedicado a funciones secundarias y llamadas al sistema operativo, como modificadores de contexto y operaciones de E/S.<br />-   En una función de llamador, la cantidad de tiempo inclusivo transcurrido de la función actual generado por llamadas de esta función de llamador.<br />-   En una función de destinatario, el tiempo dedicado a las instancias de esta función generadas por llamadas de la función actual. El valor incluye el tiempo dedicado a funciones secundarias del destinatario y llamadas al sistema operativo, como modificadores de contexto y operaciones de E/S.|  
|**Porcentaje de tiempo inclusivo transcurrido**|El porcentaje de tiempo inclusivo transcurrido total de la ejecución de generación de perfiles que se ha empleado en el tiempo inclusivo transcurrido de esta función en este contexto.|  
|**Promedio de tiempo inclusivo transcurrido**|El promedio de tiempo inclusivo transcurrido de una llamada a esta función en este contexto.|  
|**Tiempo inclusivo transcurrido máximo**|El tiempo inclusivo transcurrido máximo de una llamada a esta función en este contexto.|  
|**Tiempo inclusivo transcurrido mínimo**|El tiempo inclusivo transcurrido mínimo de una llamada a esta función en este contexto.|  
  
## <a name="elapsed-exclusive-values"></a>Valores exclusivos transcurridos  
 Los valores exclusivos transcurridos indican el tiempo que una función se estaba ejecutando directamente en la parte superior de la pila de llamadas. Incluye el tiempo dedicado a llamadas al sistema operativo, como modificadores de contexto y operaciones de E/S, pero no incluye el tiempo dedicado a funciones secundarias.  
  
|Columna|DESCRIPCIÓN|  
|------------|-----------------|  
|**Tiempo exclusivo transcurrido**|-   En la función actual, el tiempo dedicado a la ejecución directa de la función. El valor incluye el tiempo dedicado a funciones secundarias y llamadas al sistema operativo, como modificadores de contexto y operaciones de E/S.<br />-   En una función de llamador, la cantidad de tiempo exclusivo transcurrido de la función actual generado por llamadas de esta función de llamador.<br />-   En una función de destinatario, el tiempo dedicado a las instancias de esta función generadas por llamadas de la función actual. El valor no incluye el tiempo dedicado a funciones secundarias de la función de destinatario, pero incluye las llamadas al sistema operativo, como modificadores de contexto y operaciones de E/S.|  
|**Porcentaje de tiempo exclusivo transcurrido**|El porcentaje de tiempo exclusivo transcurrido total de la ejecución de generación de perfiles que se ha empleado en el tiempo exclusivo transcurrido total de esta función en este contexto.|  
|**Promedio de tiempo exclusivo transcurrido**|El promedio de tiempo exclusivo transcurrido de una llamada a esta función en este contexto.|  
|**Tiempo exclusivo transcurrido máximo**|El tiempo exclusivo transcurrido máximo de una llamada a esta función en este contexto.|  
|**Tiempo exclusivo transcurrido mínimo**|El tiempo exclusivo transcurrido mínimo de una llamada a esta función en este contexto.|  
  
## <a name="application-inclusive-values"></a>Valores inclusivos de aplicación  
 Los valores inclusivos de aplicación indican el tiempo que una función estuvo en la pila de llamadas. No incluye el tiempo dedicado a llamadas al sistema operativo, como modificadores de contexto y operaciones de E/S, pero incluye el tiempo dedicado a funciones secundarias.  
  
|Columna|DESCRIPCIÓN|  
|------------|-----------------|  
|**Tiempo inclusivo de aplicación**|-   En la función actual, el tiempo dedicado a la función y sus funciones secundarias. El valor no incluye el tiempo dedicado a llamadas al sistema operativo, como modificadores de contexto y operaciones de E/S.<br />-   En una función de llamador, la cantidad de tiempo inclusivo de aplicación de la función actual generado por llamadas de esta función de llamador.<br />-   En una función de destinatario, el tiempo dedicado a las instancias de esta función generadas por llamadas de la función actual. El valor incluye el tiempo dedicado a funciones secundarias de la función de destinatario, pero no incluye el tiempo dedicado a llamadas al sistema operativo, como modificadores de contexto y operaciones de E/S.|  
|**Porcentaje de tiempo inclusivo de aplicación**|El porcentaje de tiempo inclusivo transcurrido total de la ejecución de generación de perfiles que se ha empleado en el tiempo inclusivo de aplicación total de esta función en este contexto.|  
|**Promedio de tiempo inclusivo de aplicación**|El promedio de tiempo inclusivo de aplicación de una llamada a esta función en este contexto.|  
|**Tiempo inclusivo de aplicación máximo**|El tiempo inclusivo de aplicación máximo de una llamada a esta función en este contexto.|  
|**Tiempo inclusivo de aplicación mínimo**|El tiempo inclusivo de aplicación mínimo de una llamada a esta función en este contexto.|  
  
## <a name="application-exclusive-values"></a>Valores exclusivos de aplicación  
 Los valores exclusivos de aplicación indican el tiempo dedicado a la función. No incluye el tiempo dedicado a las funciones secundarias ni a las llamadas al sistema operativo, como modificadores de contexto y operaciones de E/S.  
  
|Columna|DESCRIPCIÓN|  
|------------|-----------------|  
|**Tiempo exclusivo de aplicación**|-   En la función actual, el tiempo dedicado a la ejecución directa de la función. El valor no incluye el tiempo dedicado a las funciones secundarias ni a las llamadas al sistema operativo, como modificadores de contexto y operaciones de E/S.<br />-   En una función de llamador, la cantidad de tiempo exclusivo de aplicación de la función actual generado por llamadas de esta función de llamador.<br />-   En una función de destinatario, el tiempo dedicado a las instancias de esta función generadas por llamadas de la función actual. El valor no incluye el tiempo dedicado a las funciones secundarias de la función de destinatario ni a las llamadas al sistema operativo, como modificadores de contexto y operaciones de E/S.|  
|**Porcentaje de tiempo exclusivo de aplicación**|El porcentaje de tiempo exclusivo transcurrido total de la ejecución de generación de perfiles que se ha empleado en el tiempo exclusivo de aplicación total de esta función en este contexto.|  
|**Promedio de tiempo exclusivo de aplicación**|El promedio de tiempo exclusivo de aplicación de una llamada a esta función en este contexto.|  
|**Tiempo exclusivo de aplicación máximo**|El tiempo exclusivo de aplicación máximo de una llamada a esta función en este contexto.|  
|**Tiempo exclusivo de aplicación mínimo**|El tiempo exclusivo de aplicación mínimo de una llamada a esta función en este contexto.|  
  
## <a name="see-also"></a>Otras referencias  
 [Cómo: Personalizar las columnas de la vista Informes](../profiling/how-to-customize-report-view-columns.md)   
 [Vista Llamador y destinatario: datos de muestreo](../profiling/caller-callee-view-sampling-data.md)   
 [Vista Llamador y destinatario: datos de muestreo de memoria de .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Vista Llamador y destinatario: datos de instrumentación de memoria de .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)
