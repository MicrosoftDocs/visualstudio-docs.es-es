---
title: 'Vista Funciones: datos de instrumentación | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Function view
ms.assetid: 595d91c8-a42b-4644-85b8-39e8140a5dfe
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ef2375fc4132e0274e7cded6daf5bdd0a58891c4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54769034"
---
# <a name="functions-view---instrumentation-data"></a>Vista Funciones: datos de instrumentación
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
|**Nombre de proceso**|Nombre del proceso.|  
|**Sobrecarga de tiempo exclusiva por sondeos**|Sobrecarga de tiempo para esta función debida a la instrumentación. No incluye la sobrecarga de las funciones a las que llamó la función. La sobrecarga por sondeos se ha restado de todos los tiempos exclusivos.|  
|**Sobrecarga de tiempo inclusiva por sondeos**|Sobrecarga de tiempo para esta función y sus funciones secundarias debida a la instrumentación. Incluye la sobrecarga de las funciones a las que llamó la función. La sobrecarga por sondeos se ha restado de todos los tiempos inclusivos.|  
  
## <a name="elapsed-inclusive-values"></a>Valores inclusivos transcurridos  
 Los valores inclusivos transcurridos indican el tiempo que una función estuvo en la pila de llamadas. Incluye el tiempo dedicado a funciones a las que llamó la función y a llamadas al sistema operativo, como modificadores de contexto y operaciones de E/S.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Tiempo inclusivo transcurrido**|Tiempo inclusivo total transcurrido para todas las llamadas a esta función.|  
|**Porcentaje de tiempo inclusivo transcurrido**|El porcentaje de tiempo inclusivo transcurrido total de la ejecución de generación de perfiles que se ha empleado en el tiempo inclusivo transcurrido de esta función.|  
|**Promedio de tiempo inclusivo transcurrido**|Promedio de tiempo inclusivo transcurrido de una llamada a esta función.|  
|**Tiempo inclusivo máximo transcurrido**|Tiempo inclusivo máximo transcurrido de una llamada a esta función.|  
|**Tiempo inclusivo transcurrido mínimo**|Tiempo inclusivo mínimo transcurrido de una llamada a esta función.|  
  
## <a name="elapsed-exclusive-values"></a>Valores exclusivos transcurridos  
 Los valores exclusivos transcurridos indican el tiempo que una función estaba ejecutando código en el cuerpo de la función, es decir, cuando la función estaba en la parte superior de la pila de llamadas. Incluye el tiempo dedicado a llamadas al sistema operativo, como modificadores de contexto y operaciones de E/S, pero no incluye el tiempo dedicado a funciones a las que llamó la función.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Tiempo exclusivo transcurrido**|Tiempo exclusivo total transcurrido para todas las llamadas a esta función.|  
|**Porcentaje de tiempo exclusivo transcurrido**|El porcentaje de tiempo exclusivo transcurrido de la generación de perfiles que se ha empleado en el tiempo exclusivo transcurrido total de esta función.|  
|**Promedio de tiempo exclusivo transcurrido**|Promedio de tiempo exclusivo transcurrido de una llamada a esta función.|  
|**Tiempo exclusivo transcurrido máximo**|Tiempo exclusivo máximo transcurrido de una llamada a esta función.|  
|**Tiempo exclusivo mínimo transcurrido**|Tiempo exclusivo mínimo transcurrido de una llamada a esta función.|  
  
## <a name="application-inclusive-values"></a>Valores inclusivos de aplicación  
 Los valores inclusivos de aplicación indican el tiempo que una función estuvo en la pila de llamadas. No incluye el tiempo dedicado a llamadas al sistema operativo, como modificadores de contexto y operaciones de E/S, pero incluye el tiempo dedicado a funciones a las que llamó la función.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Tiempo inclusivo de aplicación**|El tiempo inclusivo de aplicación total de todas las llamadas a esta función.|  
|**Porcentaje de tiempo inclusivo de aplicación**|El porcentaje de tiempo inclusivo transcurrido total de la ejecución de generación de perfiles que se ha empleado en el tiempo inclusivo de aplicación total de esta función.|  
|**Promedio de tiempo inclusivo de aplicación**|El promedio de tiempo inclusivo de aplicación de una llamada a esta función.|  
|**Tiempo inclusivo máximo de aplicación**|El tiempo inclusivo de aplicación máximo de una llamada a esta función.|  
|**Tiempo inclusivo mínimo de aplicación**|El tiempo inclusivo de aplicación mínimo de una llamada a esta función.|  
  
## <a name="application-exclusive-values"></a>Valores exclusivos de aplicación  
 Los valores exclusivos de aplicación indican el tiempo que una función se estaba ejecutando directamente en la parte superior de la pila de llamadas. No incluye el tiempo dedicado a llamadas al sistema operativo, como modificadores de contexto y operaciones de E/S, ni el tiempo dedicado a funciones a las que llamó la función.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Tiempo exclusivo de aplicación**|El tiempo exclusivo de aplicación total de todas las llamadas a esta función.|  
|**Porcentaje de tiempo exclusivo de aplicación**|El porcentaje de tiempo exclusivo transcurrido total de la ejecución de generación de perfiles que se ha empleado en el tiempo exclusivo de aplicación total de esta función.|  
|**Promedio de tiempo exclusivo de aplicación**|El promedio de tiempo exclusivo de aplicación de una llamada a esta función.|  
|**Tiempo exclusivo de aplicación máximo**|El tiempo exclusivo de aplicación máximo de una llamada a esta función.|  
|**Tiempo exclusivo mínimo de aplicación**|El tiempo exclusivo de aplicación mínimo de una llamada a esta función.|  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Personalizar las columnas de la vista de informes](../profiling/how-to-customize-report-view-columns.md)   
 [Vista Funciones](../profiling/functions-view-sampling-data.md)   
 [Vista Funciones: muestreo](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [Vista Funciones: instrumentación](../profiling/functions-view-dotnet-memory-instrumentation-data.md)
