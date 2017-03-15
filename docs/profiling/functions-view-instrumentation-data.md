---
title: "Vista Funciones: datos de instrumentación | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Function view
ms.assetid: 595d91c8-a42b-4644-85b8-39e8140a5dfe
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 2d2edf2dfc1194fa28ec99e9cbe2c500ec69859f
ms.lasthandoff: 02/22/2017

---
# <a name="functions-view---instrumentation-data"></a>Vista Funciones: datos de instrumentación
En la vista del informe de funciones se enumeran los datos de generación de perfiles por nombre de la función.  
  
## <a name="general"></a>General  
 En las columnas generales se identifica la función en una fila de la vista.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Nombre de la función**|Nombre de la función.|  
|**Dirección de la función**|Dirección de la función.|  
|**Número de línea de la función**|Número de línea del inicio de esta función en el archivo de origen.|  
|**Número de llamadas**|Número total de llamadas realizadas a esta función.|  
|**Archivo de código fuente**|Archivo de origen que contiene la definición de esta función.|  
|**Nombre del módulo**|Nombre del módulo que contiene la función.|  
|**Ruta de acceso del módulo**|Ruta de acceso del módulo que contiene la función.|  
|**Identificador del proceso**|Identificador de proceso (PID) de la ejecución de generación de perfiles.|  
|**Nombre del proceso**|Nombre del proceso.|  
|**Sobrecarga de tiempo exclusiva por sondeos**|Sobrecarga de tiempo para esta función debida a la instrumentación. No incluye la sobrecarga de las funciones a las que llamó la función. La sobrecarga por sondeos se ha restado de todos los tiempos exclusivos.|  
|**Sobrecarga de tiempo inclusiva por sondeos**|Sobrecarga de tiempo para esta función y sus funciones secundarias debida a la instrumentación. Incluye la sobrecarga de las funciones a las que llamó la función. La sobrecarga por sondeos se ha restado de todos los tiempos inclusivos.|  
  
## <a name="elapsed-inclusive-values"></a>Valores inclusivos transcurridos  
 Los valores inclusivos transcurridos indican el tiempo que una función estuvo en la pila de llamadas. Incluye el tiempo dedicado a funciones a las que llamó la función y a llamadas al sistema operativo, como modificadores de contexto y operaciones de E/S.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Tiempo inclusivo transcurrido**|Tiempo inclusivo total transcurrido para todas las llamadas a esta función.|  
|**Porcentaje de tiempo inclusivo transcurrido**|El porcentaje de tiempo inclusivo transcurrido total de la ejecución de generación de perfiles que se ha empleado en el tiempo inclusivo transcurrido de esta función.|  
|**Promedio de tiempo inclusivo transcurrido**|Promedio de tiempo inclusivo transcurrido de una llamada a esta función.|  
|**Tiempo inclusivo transcurrido máximo**|Tiempo inclusivo máximo transcurrido de una llamada a esta función.|  
|**Tiempo inclusivo transcurrido mínimo**|Tiempo inclusivo mínimo transcurrido de una llamada a esta función.|  
  
## <a name="elapsed-exclusive-values"></a>Valores exclusivos transcurridos  
 Los valores exclusivos transcurridos indican el tiempo que una función estaba ejecutando código en el cuerpo de la función, es decir, cuando la función estaba en la parte superior de la pila de llamadas. Incluye el tiempo dedicado a llamadas al sistema operativo, como modificadores de contexto y operaciones de E/S, pero no incluye el tiempo dedicado a funciones a las que llamó la función.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Tiempo exclusivo transcurrido**|Tiempo exclusivo total transcurrido para todas las llamadas a esta función.|  
|**Porcentaje de tiempo exclusivo transcurrido**|El porcentaje de tiempo exclusivo transcurrido de la generación de perfiles que se ha empleado en el tiempo exclusivo transcurrido total de esta función.|  
|**Promedio de tiempo exclusivo transcurrido**|Promedio de tiempo exclusivo transcurrido de una llamada a esta función.|  
|**Tiempo exclusivo transcurrido máximo**|Tiempo exclusivo máximo transcurrido de una llamada a esta función.|  
|**Tiempo exclusivo transcurrido mínimo**|Tiempo exclusivo mínimo transcurrido de una llamada a esta función.|  
  
## <a name="application-inclusive-values"></a>Valores inclusivos de aplicación  
 Los valores inclusivos de aplicación indican el tiempo que una función estuvo en la pila de llamadas. No incluye el tiempo dedicado a llamadas al sistema operativo, como modificadores de contexto y operaciones de E/S, pero incluye el tiempo dedicado a funciones a las que llamó la función.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Tiempo inclusivo de aplicación**|El tiempo inclusivo de aplicación total de todas las llamadas a esta función.|  
|**Porcentaje de tiempo inclusivo de aplicación**|El porcentaje de tiempo inclusivo transcurrido total de la ejecución de generación de perfiles que se ha empleado en el tiempo inclusivo de aplicación total de esta función.|  
|**Promedio de tiempo inclusivo de aplicación**|El promedio de tiempo inclusivo de aplicación de una llamada a esta función.|  
|**Tiempo inclusivo de aplicación máximo**|El tiempo inclusivo de aplicación máximo de una llamada a esta función.|  
|**Tiempo inclusivo de aplicación mínimo**|El tiempo inclusivo de aplicación mínimo de una llamada a esta función.|  
  
## <a name="application-exclusive-values"></a>Valores exclusivos de aplicación  
 Los valores exclusivos de aplicación indican el tiempo que una función se estaba ejecutando directamente en la parte superior de la pila de llamadas. No incluye el tiempo dedicado a llamadas al sistema operativo, como modificadores de contexto y operaciones de E/S, ni el tiempo dedicado a funciones a las que llamó la función.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Tiempo exclusivo de aplicación**|El tiempo exclusivo de aplicación total de todas las llamadas a esta función.|  
|**Porcentaje de tiempo exclusivo de aplicación**|El porcentaje de tiempo exclusivo transcurrido total de la ejecución de generación de perfiles que se ha empleado en el tiempo exclusivo de aplicación total de esta función.|  
|**Promedio de tiempo exclusivo de aplicación**|El promedio de tiempo exclusivo de aplicación de una llamada a esta función.|  
|**Tiempo exclusivo de aplicación máximo**|El tiempo exclusivo de aplicación máximo de una llamada a esta función.|  
|**Tiempo exclusivo de aplicación mínimo**|El tiempo exclusivo de aplicación mínimo de una llamada a esta función.|  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Personalizar las columnas de la vista Informes](../profiling/how-to-customize-report-view-columns.md)   
 [Vista Funciones](../profiling/functions-view-sampling-data.md)   
 [Vista Funciones: muestreo](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [Vista Funciones: instrumentación](../profiling/functions-view-dotnet-memory-instrumentation-data.md)
