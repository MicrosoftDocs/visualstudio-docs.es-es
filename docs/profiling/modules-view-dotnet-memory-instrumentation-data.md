---
title: 'Vista Módulos: datos de instrumentación de memoria de .NET | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Modules view
ms.assetid: 26516139-0981-41de-917d-ad5769391b8d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: a0dd74f25ed5dc7f76b9d35ae3d2d9833f8e4ab8
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2018
ms.locfileid: "35255530"
---
# <a name="modules-view---net-memory-instrumentation-data"></a>Vista Módulos: datos de instrumentación de memoria de .NET
La vista Módulos de los datos de asignación de memoria de .NET recopilados con el método de instrumentación agrupa los datos de tiempo y memoria por los módulos que se ejecutaron durante la generación de perfiles. Los datos de generación de perfiles de las funciones del módulo se enumeran bajo el nodo de módulo.  
  
## <a name="general"></a>General  
  
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
  
## <a name="net-memory-values"></a>Valores de memoria de .NET  
 Los valores de memoria de .NET inclusivos de una función indican el número (asignaciones) y el tamaño (bytes) de objetos creados por la función y sus funciones secundarias.  
  
 Los valores de memoria exclusivos indican el número y el tamaño de objetos creados por la función y no por sus funciones secundarias.  
  
 Los valores inclusivos y exclusivos de memoria de un módulo son la suma de los valores de memoria inclusivos y exclusivos de las funciones del módulo.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Asignaciones inclusivas**|-   Para una función, el número total de objetos creados por la función. Este número incluye los objetos creados por las funciones llamadas por la función.<br />-   Para un módulo, el número de objetos en una generación de perfiles asignados cuando se estaba ejecutando al menos una función del módulo. Este número incluye los objetos asignados en funciones generadas por las llamadas de funciones del módulo.|  
|**Porcentaje de asignaciones inclusivas**|El porcentaje de todos los objetos que se asignaron durante la generación de perfiles que son asignaciones inclusivas del módulo o la función.|  
|**Asignaciones exclusivas**|-   Para una función, el número de objetos creados cuando la función estaba ejecutando código en el cuerpo de función (es decir, cuando la función estaba en la parte superior de la pila de llamadas). Este número no incluye los objetos creados en las funciones llamadas por la función.<br />-   Para un módulo, la suma de las asignaciones exclusivas de las funciones del módulo.|  
|**Porcentaje de asignaciones exclusivas**|El porcentaje de todos los objetos que se asignaron durante la generación de perfiles que son asignaciones exclusivas del módulo o la función.|  
|**Bytes exclusivos**|-   Para una función, el número total de bytes de memoria asignados cuando la función estaba ejecutando el código en el cuerpo de función (es decir, cuando la función estaba en la parte superior de la pila de llamadas). Este número no incluye los bytes asignados en las funciones llamadas por la función.<br />-   Para un módulo, la suma de bytes exclusivos que fueron asignados por las funciones del módulo.|  
|**Porcentaje de bytes exclusivos**|El porcentaje de todos los bytes que se asignaron durante la generación de perfiles que son bytes exclusivos del módulo, función, línea o instrucción.|  
|**Porcentaje de bytes inclusivos**|-   Para una función, el número de bytes asignados por la función. Este número incluye los bytes asignados en las funciones llamadas por la función.<br />-   Para un módulo, el número de bytes asignados en una generación de perfiles que se asignaron cuando se estaba ejecutando al menos una función del módulo. Este número incluye los objetos creados en todas las funciones llamadas por las funciones del módulo.|  
|**Porcentaje de bytes inclusivos**|El porcentaje de todos los bytes que se asignaron durante la generación de perfiles que son bytes inclusivos del módulo o la función.|  
  
## <a name="elapsed-inclusive-values"></a>Valores de tiempo inclusivo transcurrido  
 Los valores inclusivos transcurridos indican el tiempo que una función estuvo en la pila de llamadas. Incluye el tiempo dedicado a funciones secundarias y llamadas al sistema operativo, como modificadores de contexto y operaciones de E/S.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Tiempo inclusivo transcurrido**|-   Para una función, el tiempo dedicado a la función. Incluye el tiempo dedicado a funciones secundarias y llamadas al sistema operativo, como cambios de contexto y operaciones de E/S.<br />-   Para un módulo, el período de tiempo en el que al menos una función del módulo estuvo en la pila de llamadas.|  
|**Porcentaje de tiempo inclusivo transcurrido**|El porcentaje de tiempo total inclusivo transcurrido de la generación de perfiles que se ha empleado en el tiempo inclusivo transcurrido total de este módulo o función.|  
|**Promedio de tiempo inclusivo transcurrido**|-   Para una función, el promedio de tiempo inclusivo transcurrido de una llamada a esta función.<br />-   Para un módulo, el promedio de tiempo inclusivo transcurrido de todas las llamadas a las funciones del módulo.|  
|**Tiempo inclusivo máximo transcurrido**|-   Para una función, el tiempo inclusivo máximo transcurrido de una llamada a esta función.<br />-   Para un módulo, el tiempo inclusivo máximo transcurrido de todas las llamadas a las funciones del módulo.|  
|**Tiempo inclusivo mínimo transcurrido**|-   Para una función, el tiempo inclusivo mínimo transcurrido de una llamada a este módulo o función.<br />-   Para un módulo, el tiempo inclusivo mínimo transcurrido de todas las llamadas a las funciones del módulo.|  
  
## <a name="elapsed-exclusive-values"></a>Valores de tiempo exclusivo transcurrido  
 Los valores exclusivos transcurridos indican el tiempo que una función se estaba ejecutando directamente en la parte superior de la pila de llamadas. Incluye el tiempo dedicado llamadas al sistema operativo, como cambios de contexto y operaciones de E/S, pero no incluye el tiempo dedicado a funciones secundarias.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Tiempo exclusivo transcurrido**|-   Para una función, el tiempo dedicado al módulo o la función. Incluye el tiempo dedicado a llamadas al sistema operativo, como cambios de contexto y operaciones de E/S, pero excluye el tiempo dedicado a funciones secundarias.<br />-   Para un módulo, la suma del tiempo exclusivo transcurrido de las funciones del módulo.|  
|**Porcentaje de tiempo exclusivo transcurrido**|El porcentaje de tiempo exclusivo transcurrido de la generación de perfiles que se ha empleado en el tiempo exclusivo transcurrido total de este módulo o función.|  
|**Promedio de tiempo exclusivo transcurrido**|-   Para una función, el promedio de tiempo exclusivo transcurrido de una llamada a esta función.<br />-   Para un módulo, el promedio de tiempo exclusivo transcurrido de todas las llamadas a las funciones del módulo.|  
|**Tiempo exclusivo máximo transcurrido**|-   Para una función, el tiempo exclusivo máximo transcurrido de una llamada a esta función.<br />-   Para un módulo, el tiempo exclusivo máximo transcurrido de todas las llamadas a las funciones del módulo.|  
|**Tiempo exclusivo mínimo transcurrido**|-   Para una función, el tiempo exclusivo mínimo transcurrido de una llamada a este módulo o función.<br />-   Para un módulo, el tiempo exclusivo mínimo transcurrido de todas las llamadas a las funciones del módulo.|  
  
## <a name="application-inclusive-values"></a>Valores de tiempo inclusivo de aplicación  
 Los valores inclusivos de aplicación indican el tiempo que una función estuvo en la pila de llamadas. No incluye el tiempo dedicado a llamadas al sistema operativo, como modificadores de contexto y operaciones de E/S, pero incluye el tiempo dedicado a funciones secundarias.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Tiempo inclusivo de aplicación**|-   Para una función, el tiempo dedicado a llamadas a la función. Incluye el tiempo dedicado a las funciones secundarias pero excluye las llamadas al sistema operativo, como cambios de contexto y operaciones de E/S.<br />-   Para un módulo, el período de tiempo en el que al menos una función del módulo estuvo en la pila de llamadas, excluido el tiempo dedicado a llamadas al sistema operativo.|  
|**Porcentaje de tiempo inclusivo de aplicación**|El porcentaje de tiempo inclusivo transcurrido de la generación de perfiles que se ha empleado en el tiempo inclusivo de aplicación de este módulo o función.|  
|**Promedio de tiempo inclusivo de aplicación**|-   Para una función, el promedio de tiempo inclusivo de aplicación de una llamada a esta función.<br />-   Para un módulo, el promedio de tiempo inclusivo de aplicación de todas las llamadas a las funciones del módulo.|  
|**Tiempo inclusivo máximo de aplicación**|-   Para una función, el tiempo inclusivo máximo de aplicación de una llamada a esta función.<br />-   Para un módulo, el tiempo inclusivo máximo de aplicación de todas las llamadas a las funciones del módulo.|  
|**Tiempo inclusivo mínimo de aplicación**|-   Para una función, el tiempo inclusivo mínimo de aplicación de una llamada a este módulo o función.<br />-   Para un módulo, el tiempo inclusivo mínimo de aplicación de todas las llamadas a las funciones del módulo.|  
  
## <a name="application-exclusive-values"></a>Valores de tiempo exclusivo de aplicación  
 Los valores exclusivos de aplicación indican el tiempo dedicado al módulo o la función, excluyendo el tiempo dedicado a funciones secundarias. El tiempo indicado también excluye las llamadas al sistema operativo, como cambios de contexto y operaciones de E/S.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Tiempo exclusivo de aplicación**|-   Para una función, el tiempo exclusivo de aplicación total de llamadas a esta función.<br />-   Para un módulo, el tiempo exclusivo total de aplicación de todas las llamadas a las funciones del módulo.|  
|**Porcentaje de tiempo exclusivo de aplicación**|El porcentaje de tiempo exclusivo transcurrido de la generación de perfiles que se ha empleado en el tiempo exclusivo de aplicación de este módulo o función.|  
|**Promedio de tiempo exclusivo de aplicación**|-   Para una función, el promedio de tiempo exclusivo de aplicación de una llamada a esta función.<br />-   Para un módulo, el promedio de tiempo exclusivo de aplicación de todas las llamadas a las funciones del módulo.|  
|**Tiempo exclusivo máximo de aplicación**|-   Para una función, el tiempo exclusivo máximo de aplicación de una llamada a esta función.<br />-   Para un módulo, el tiempo exclusivo máximo de aplicación de todas las llamadas a las funciones del módulo.|  
|**Tiempo exclusivo mínimo de aplicación**|-   Para una función, el tiempo exclusivo mínimo de aplicación de una llamada a este módulo o función.<br />-   Para un módulo, el tiempo exclusivo mínimo de aplicación de todas las llamadas a las funciones del módulo.|  
  
## <a name="see-also"></a>Vea también  
 [Vista Módulos: muestreo](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [Vista Módulos](../profiling/modules-view-instrumentation-data.md)   
 [Vista Módulos](../profiling/modules-view-sampling-data.md)