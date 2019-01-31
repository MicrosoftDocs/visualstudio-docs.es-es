---
title: 'Vista Módulos: datos de instrumentación | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Modules view
ms.assetid: 895b9589-1987-4160-916f-53b898a69cf0
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4455f850ad533f17cd9f6cb33e7e874621d0bb2c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54787686"
---
# <a name="modules-view---instrumentation-data"></a>Vista Módulos: datos de instrumentación
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La vista Módulos muestra datos de rendimiento agrupados por los módulos incluidos en los datos de generación de perfiles. Las funciones del módulo se enumeran bajo el nodo de módulo.  
  
## <a name="general"></a>General  
 En las columnas generales se identifica la función en una fila de la vista.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Name**|Nombre de la función o el módulo.|  
|**Número de línea de función**|Número de línea del inicio de esta función en el archivo de origen.|  
|**Número de llamadas**|Número total de llamadas realizadas a esta función o módulo.|  
|**Archivo de código fuente**|Archivo de origen que contiene la definición de esta función.|  
|**Nombre del módulo**|Nombre del módulo que contiene la función.|  
|**Ruta de acceso del módulo**|Ruta de acceso del módulo que contiene la función.|  
|**Identificador del proceso**|Identificador de proceso (PID) de la ejecución de generación de perfiles.|  
|**Nombre de proceso**|Nombre del proceso en el que se estaba ejecutando el módulo o la función.|  
|**Sobrecarga de tiempo exclusiva por sondeos**|Sobrecarga de tiempo para esta función o módulo debida a la instrumentación.|  
|**Sobrecarga de tiempo inclusiva por sondeos**|Sobrecarga de tiempo para esta función o módulo y sus funciones secundarias debida a la instrumentación.|  
  
## <a name="elapsed-inclusive-values"></a>Valores inclusivos transcurridos  
 Los valores inclusivos transcurridos indican el tiempo que una función estuvo en la pila de llamadas. Incluye el tiempo dedicado a funciones secundarias y llamadas al sistema operativo, como modificadores de contexto y operaciones de E/S.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Tiempo inclusivo transcurrido**|-   Para una función, el tiempo dedicado a la función. Incluye el tiempo dedicado a funciones secundarias y llamadas al sistema operativo, como cambios de contexto y operaciones de E/S.<br />-   Para un módulo, el tiempo en el que al menos una función del módulo estuvo en la pila de llamadas.|  
|**Porcentaje de tiempo inclusivo transcurrido**|El porcentaje de tiempo total inclusivo transcurrido de la generación de perfiles que se ha empleado en el tiempo inclusivo transcurrido total de este módulo o función.|  
|**Promedio de tiempo inclusivo transcurrido**|-   Para una función, el promedio de tiempo inclusivo transcurrido de una llamada a esta función.<br />-   Para un módulo, el promedio de tiempo inclusivo transcurrido de todas las llamadas a las funciones del módulo.|  
|**Tiempo inclusivo máximo transcurrido**|-   Para una función, el tiempo inclusivo máximo transcurrido de una llamada a esta función.<br />-   Para un módulo, el tiempo inclusivo máximo transcurrido de todas las llamadas a las funciones del módulo.|  
|**Tiempo inclusivo mínimo transcurrido**|-   Para una función, el tiempo inclusivo mínimo transcurrido de una llamada a este módulo o función.<br />-   Para un módulo, el tiempo inclusivo mínimo transcurrido de todas las llamadas a las funciones del módulo.|  
  
## <a name="elapsed-exclusive-values"></a>Valores exclusivos transcurridos  
 Los valores exclusivos transcurridos indican el tiempo que una función se estaba ejecutando directamente en la parte superior de la pila de llamadas. Incluye el tiempo dedicado a llamadas al sistema operativo, como modificadores de contexto y operaciones de E/S, pero no incluye el tiempo dedicado a funciones secundarias.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Tiempo exclusivo transcurrido**|-   Para una función, el tiempo dedicado al módulo o la función. Incluye el tiempo dedicado a llamadas al sistema operativo, como cambios de contexto y operaciones de E/S, pero excluye el tiempo dedicado a funciones secundarias.<br />-   Para un módulo, la suma del tiempo exclusivo transcurrido de las funciones del módulo.|  
|**Porcentaje de tiempo exclusivo transcurrido**|El porcentaje de tiempo exclusivo transcurrido de la generación de perfiles que se ha empleado en el tiempo exclusivo transcurrido total de este módulo o función.|  
|**Promedio de tiempo exclusivo transcurrido**|-   Para una función, el promedio de tiempo exclusivo transcurrido de una llamada a esta función.<br />-   Para un módulo, el promedio de tiempo exclusivo transcurrido de todas las llamadas a las funciones del módulo.|  
|**Tiempo exclusivo máximo transcurrido**|-   Para una función, el tiempo exclusivo máximo transcurrido de una llamada a esta función.<br />-   Para un módulo, el tiempo exclusivo máximo transcurrido de todas las llamadas a las funciones del módulo.|  
|**Tiempo exclusivo mínimo transcurrido**|-   Para una función, el tiempo exclusivo mínimo transcurrido de una llamada a este módulo o función.<br />-   Para un módulo, el tiempo exclusivo mínimo transcurrido de todas las llamadas a las funciones del módulo.|  
  
## <a name="application-inclusive-values"></a>Valores inclusivos de aplicación  
 Los valores inclusivos de aplicación indican el tiempo que estuvo una función en la pila de llamadas. No incluye el tiempo dedicado llamadas al sistema operativo, como cambios de contexto y operaciones de E/S. Sin embargo, incluye el tiempo dedicado a funciones secundarias.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Tiempo inclusivo de aplicación**|-   Para una función, el tiempo dedicado a llamadas a la función. Incluye el tiempo dedicado a las funciones secundarias pero excluye las llamadas al sistema operativo, como cambios de contexto y operaciones de E/S.<br />-   Para un módulo, el tiempo en el que al menos una función del módulo estuvo en la pila de llamadas. Excluye el tiempo dedicado a llamadas al sistema operativo.|  
|**Porcentaje de tiempo inclusivo de aplicación**|El porcentaje de tiempo inclusivo transcurrido de la generación de perfiles que se ha empleado en el tiempo inclusivo de aplicación de este módulo o función.|  
|**Promedio de tiempo inclusivo de aplicación**|-   Para una función, el promedio de tiempo inclusivo de aplicación de una llamada a esta función.<br />-   Para un módulo, el promedio de tiempo inclusivo de aplicación de todas las llamadas a las funciones del módulo.|  
|**Tiempo inclusivo máximo de aplicación**|-   Para una función, el tiempo inclusivo máximo de aplicación de una llamada a esta función.<br />-   Para un módulo, el tiempo inclusivo máximo de aplicación de todas las llamadas a las funciones del módulo.|  
|**Tiempo inclusivo mínimo de aplicación**|-   Para una función, el tiempo inclusivo mínimo de aplicación de una llamada a este módulo o función.<br />-   Para un módulo, el tiempo inclusivo mínimo de aplicación de todas las llamadas a las funciones del módulo.|  
  
## <a name="application-exclusive-values"></a>Valores exclusivos de aplicación  
 Los valores exclusivos de aplicación indican el tiempo dedicado al módulo o la función. Excluye el tiempo dedicado a las funciones secundarias y las llamadas al sistema operativo, como cambios de contexto y operaciones de E/S.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Tiempo exclusivo de aplicación**|El tiempo exclusivo de aplicación total de todas llamadas a este módulo o función.|  
|**Porcentaje de tiempo exclusivo de aplicación**|El porcentaje de tiempo exclusivo transcurrido de la generación de perfiles que se ha empleado en el tiempo exclusivo de aplicación de este módulo o función.|  
|**Promedio de tiempo exclusivo de aplicación**|-   Para una función, el promedio de tiempo exclusivo de aplicación de una llamada a esta función.<br />-   Para un módulo, el promedio de tiempo exclusivo de aplicación de todas las llamadas a las funciones del módulo.|  
|**Tiempo exclusivo máximo de aplicación**|-   Para una función, el tiempo exclusivo máximo de aplicación de una llamada a esta función.<br />-   Para un módulo, el tiempo exclusivo máximo de aplicación de todas las llamadas a las funciones del módulo.|  
|**Tiempo exclusivo mínimo de aplicación**|-   Para una función, el tiempo exclusivo mínimo de aplicación de una llamada a este módulo o función.<br />-   Para un módulo, el tiempo exclusivo mínimo de aplicación de todas las llamadas a las funciones del módulo.|  
  
## <a name="see-also"></a>Vea también  
 [Vista Módulos](../profiling/modules-view-sampling-data.md)   
 [Vista Módulos: instrumentación](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Vista Módulos: muestreo](../profiling/modules-view-dotnet-memory-sampling-data.md)
