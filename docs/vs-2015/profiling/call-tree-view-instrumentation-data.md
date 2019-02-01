---
title: 'Vista Árbol de llamadas: datos de instrumentación | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Call Tree view
ms.assetid: 306bd176-0ce9-4a10-89ca-20b043d37d4e
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 385d12550692f5f27521afe4dea12e5bdb0aa9d8
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54782393"
---
# <a name="call-tree-view---instrumentation-data"></a>Vista Árbol de llamadas: datos de instrumentación
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los valores de una función en la vista Árbol de llamadas indican el tiempo de las instancias de la función a las que llamó la función primaria en el árbol de llamadas. Los valores de porcentaje se calculan comparando el valor de las instancias de la función con el tiempo inclusivo transcurrido total de todas las funciones de la ejecución de generación de perfiles.  
  
## <a name="general"></a>General  
 En las columnas generales se identifica la función en una fila de la vista.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Nombre de la función**|Nombre de la función.|  
|**Dirección de la función**|Dirección de la función.|  
|**Número de línea de la función**|Número de línea del inicio de esta función en el archivo de origen.|  
|**Número de llamadas**|El número total de llamadas realizadas a esta función.|  
|**Archivo de código fuente**|Archivo de origen que contiene la definición de esta función.|  
|**Nombre del módulo**|Nombre del módulo que contiene la función.|  
|**Ruta de acceso del módulo**|Ruta de acceso del módulo que contiene la función.|  
|**Identificador del proceso**|Identificador de proceso (PID) de la ejecución de generación de perfiles.|  
|**Nombre del proceso**|El nombre que se asigna al proceso.|  
|**Sobrecarga de tiempo exclusiva por sondeos**|Sobrecarga de tiempo para esta función debida a la instrumentación. La sobrecarga por sondeos se ha restado de todos los tiempos exclusivos.|  
|**Sobrecarga de tiempo inclusiva por sondeos**|Sobrecarga de tiempo para esta función y sus funciones secundarias debida a la instrumentación. La sobrecarga por sondeos se ha restado de todos los tiempos inclusivos.|  
|**Nivel**|La profundidad de esta función en el árbol de llamadas. Solo disponible en los informes de línea de comandos de [VSPerfReport](../profiling/vsperfreport.md).|  
  
## <a name="elapsed-inclusive-values"></a>Valores inclusivos transcurridos  
 Los valores inclusivos transcurridos indican el tiempo en la pila de llamadas de esas instancias de la función a las que llamó la función primaria en el árbol de llamadas. Incluye el tiempo dedicado a funciones secundarias a las que llamó la función y a llamadas al sistema operativo, como modificadores de contexto y operaciones de E/S.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Tiempo inclusivo transcurrido**|El tiempo inclusivo transcurrido total de todas las llamadas a esta función en este contexto.|  
|**Porcentaje de tiempo inclusivo transcurrido**|El porcentaje de tiempo inclusivo transcurrido total de la ejecución de generación de perfiles que se ha empleado en el tiempo inclusivo transcurrido total de esta función en este contexto.|  
|**Promedio de tiempo inclusivo transcurrido**|El promedio de tiempo inclusivo transcurrido de una llamada a esta función en este contexto.|  
|**Tiempo inclusivo transcurrido máximo**|El tiempo inclusivo transcurrido máximo de una llamada a esta función en este contexto.|  
|**Tiempo inclusivo transcurrido mínimo**|El tiempo inclusivo transcurrido mínimo de una llamada a esta función en este contexto.|  
  
## <a name="elapsed-exclusive-values"></a>Valores exclusivos transcurridos  
 Los valores exclusivos transcurridos indican el tiempo que las instancias de una función a las que llamó la función primaria en el árbol de llamadas ejecutaron código en el cuerpo de la función; es decir, cuando la función estaba en la parte superior de la pila de llamadas. El tiempo también incluye el tiempo dedicado a las llamadas al sistema operativo, como modificadores de contexto y operaciones de E/S. Sin embargo, el tiempo no incluye el tiempo dedicado a funciones secundarias a las que llamó la función.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Tiempo exclusivo transcurrido**|El tiempo exclusivo transcurrido total de todas las llamadas a esta función en este contexto.|  
|**Porcentaje de tiempo exclusivo transcurrido**|El porcentaje de tiempo exclusivo transcurrido total de la ejecución de generación de perfiles que se ha empleado en el tiempo exclusivo transcurrido total de esta función en este contexto.|  
|**Promedio de tiempo exclusivo transcurrido**|El promedio de tiempo exclusivo transcurrido de una llamada a esta función en este contexto.|  
|**Tiempo exclusivo transcurrido máximo**|El tiempo exclusivo transcurrido máximo de una llamada a esta función en este contexto.|  
|**Tiempo exclusivo transcurrido mínimo**|El tiempo exclusivo transcurrido mínimo de una llamada a esta función en este contexto.|  
  
## <a name="application-inclusive-values"></a>Valores inclusivos de aplicación  
 Los valores inclusivos de aplicación indican el tiempo que las instancias de una función a las que llamó la función primaria en el árbol de llamadas permanecieron en la pila de llamadas. El tiempo no incluye el tiempo dedicado a llamadas al sistema operativo, como modificadores de contexto y operaciones de E/S. Sin embargo, incluye el tiempo dedicado a funciones secundarias a las que llamó la función.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Tiempo inclusivo de aplicación**|El tiempo inclusivo de aplicación total de todas las llamadas a esta función en este contexto.|  
|**Porcentaje de tiempo inclusivo de aplicación**|El porcentaje de tiempo inclusivo transcurrido total de la ejecución de generación de perfiles que se ha empleado en el tiempo inclusivo de aplicación total de esta función en este contexto.|  
|**Promedio de tiempo inclusivo de aplicación**|El promedio de tiempo inclusivo de aplicación de una llamada a esta función en este contexto.|  
|**Tiempo inclusivo de aplicación máximo**|El tiempo inclusivo de aplicación máximo de una llamada a esta función en este contexto.|  
|**Tiempo inclusivo de aplicación mínimo**|El tiempo inclusivo de aplicación mínimo de una llamada a esta función en este contexto.|  
  
## <a name="application-exclusive-values"></a>Valores exclusivos de aplicación  
 Los valores exclusivos de aplicación indican el tiempo que las instancias de una función a las que llamó la función primaria en el árbol de llamadas ejecutaron directamente código en el cuerpo de la función; es decir, cuando la función estaba en la parte superior de la pila de llamadas. No incluye el tiempo dedicado a llamadas al sistema operativo, como cambios de contexto y operaciones de E/S. Tampoco incluye el tiempo dedicado a funciones secundarias a las que llamó la función.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Tiempo exclusivo de aplicación**|El tiempo exclusivo de aplicación total de todas las llamadas a esta función en este contexto.|  
|**Porcentaje de tiempo exclusivo de aplicación**|El porcentaje de tiempo exclusivo transcurrido total de la ejecución de generación de perfiles que se ha empleado en el tiempo exclusivo de aplicación total de esta función en este contexto.|  
|**Promedio de tiempo exclusivo de aplicación**|El promedio de tiempo exclusivo de aplicación de una llamada a esta función en este contexto.|  
|**Tiempo exclusivo de aplicación máximo**|El tiempo exclusivo de aplicación máximo de una llamada a esta función en este contexto.|  
|**Tiempo exclusivo de aplicación mínimo**|El tiempo exclusivo de aplicación mínimo de una llamada a esta función en este contexto.|  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Personalizar las columnas de la vista de informes](../profiling/how-to-customize-report-view-columns.md)   
 [Vista Árbol de llamadas](../profiling/call-tree-view-sampling-data.md)   
 [Vista Árbol de llamadas: instrumentación](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Vista Árbol de llamadas: muestreo](../profiling/call-tree-view-dotnet-memory-sampling-data.md)
