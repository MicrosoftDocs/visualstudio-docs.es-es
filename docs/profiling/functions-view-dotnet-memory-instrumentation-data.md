---
title: 'Vista Funciones: Datos de instrumentación de memoria de .NET | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Functions view
ms.assetid: cd45b379-394b-4b71-828c-92cd89e46ae0
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: eba1f0d1434d253aaca698d3ae582e3c507c2d23
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779238"
---
# <a name="functions-view---net-memory-instrumentation-data"></a>Vista Funciones: Datos de instrumentación de memoria de .NET
La vista Funciones de los datos de generación de perfiles de asignación de memoria de .NET que se recopilaron mediante el método de instrumentación enumera las funciones que asignaron memoria durante la generación de perfiles. Una fila de función indica el tamaño y el número de asignaciones y los datos de tiempo para la función.

## <a name="general"></a>General

|Columna|DESCRIPCIÓN|
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
|**Sobrecarga de tiempo exclusiva por sondeos**|Sobrecarga de tiempo para esta función debida a la instrumentación. La sobrecarga por sondeos se ha restado de todos los tiempos exclusivos.|
|**Sobrecarga de tiempo inclusiva por sondeos**|Sobrecarga de tiempo para esta función y sus funciones secundarias debida a la instrumentación. La sobrecarga por sondeos se ha restado de todos los tiempos inclusivos.|

## <a name="net-memory-values"></a>Valores de memoria de .NET
 Los valores de memoria de .NET inclusivos de una función indican el número (asignaciones) y el tamaño (bytes) de objetos creados por la función y sus funciones secundarias.

 Los valores de memoria exclusivos indican el número y el tamaño de objetos creados por la función y no por sus funciones secundarias.

|Columna|DESCRIPCIÓN|
|------------|-----------------|
|**Asignaciones inclusivas**|Número total de objetos creados en esta función y en funciones a las que llamó esta función.|
|**Porcentaje de asignaciones inclusivas**|Porcentaje de todos los objetos que se asignaron durante la ejecución de la generación de perfiles que eran asignaciones inclusivas de esta función.|
|**Asignaciones exclusivas**|Número total de objetos creados cuando la función estaba ejecutando código en el cuerpo de la función. Este número no incluye los objetos creados en las funciones a las que llamó esta función.|
|**Porcentaje de asignaciones exclusivas**|El porcentaje de todos los objetos que se crearon durante la ejecución de la generación de perfiles que eran asignaciones exclusivas de esta función.|
|**Porcentaje de bytes inclusivos**|Número de bytes de memoria que se asignaron en esta función y en funciones a las que llamó esta función.|
|**Porcentaje de bytes inclusivos**|Porcentaje de todos los bytes de memoria que se asignaron durante la ejecución de la generación de perfiles que eran bytes inclusivos de esta función.|
|**Bytes exclusivos**|Número de bytes de memoria asignados por esta función, pero no por funciones a las que llamó esta función.|
|**Porcentaje de bytes exclusivos**|Porcentaje de todos los bytes de memoria que se asignaron durante la ejecución de la generación de perfiles que eran bytes exclusivos de esta función.|

## <a name="elapsed-inclusive-values"></a>Valores de tiempo inclusivo transcurrido
 Los valores inclusivos transcurridos indican el tiempo que una función estuvo en la pila de llamadas. Incluye el tiempo dedicado a funciones secundarias y llamadas al sistema operativo, como modificadores de contexto y operaciones de E/S.

|Columna|DESCRIPCIÓN|
|------------|-----------------|
|**Tiempo inclusivo transcurrido**|Tiempo inclusivo total transcurrido para todas las llamadas a esta función.|
|**Porcentaje de tiempo inclusivo transcurrido**|El porcentaje de tiempo inclusivo transcurrido total de la ejecución de generación de perfiles que se ha empleado en el tiempo inclusivo transcurrido de esta función.|
|**Promedio de tiempo inclusivo transcurrido**|Promedio de tiempo inclusivo transcurrido de una llamada a esta función.|
|**Tiempo inclusivo máximo transcurrido**|Tiempo inclusivo máximo transcurrido de una llamada a esta función.|
|**Tiempo inclusivo transcurrido mínimo**|Tiempo inclusivo mínimo transcurrido de una llamada a esta función.|

## <a name="elapsed-exclusive-values"></a>Valores de tiempo exclusivo transcurrido
 Los valores exclusivos transcurridos indican el tiempo que una función se estaba ejecutando directamente en la parte superior de la pila de llamadas. Incluye el tiempo dedicado llamadas al sistema operativo, como modificadores de contexto y operaciones de E/S, pero no incluye el tiempo dedicado a funciones secundarias.

|Columna|DESCRIPCIÓN|
|------------|-----------------|
|**Tiempo exclusivo transcurrido**|Tiempo exclusivo total transcurrido para todas las llamadas a esta función.|
|**Porcentaje de tiempo exclusivo transcurrido**|El porcentaje de tiempo exclusivo transcurrido de la generación de perfiles que se ha empleado en el tiempo exclusivo transcurrido total de esta función.|
|**Promedio de tiempo exclusivo transcurrido**|Promedio de tiempo exclusivo transcurrido de una llamada a esta función.|
|**Tiempo exclusivo transcurrido máximo**|Tiempo exclusivo máximo transcurrido de una llamada a esta función.|
|**Tiempo exclusivo mínimo transcurrido**|Tiempo exclusivo mínimo transcurrido de una llamada a esta función.|

## <a name="application-inclusive-values"></a>Valores de tiempo inclusivo de aplicación
 Los valores inclusivos de aplicación indican el tiempo que una función estuvo en la pila de llamadas. No incluye el tiempo dedicado a llamadas al sistema operativo, como modificadores de contexto y operaciones de E/S, pero incluye el tiempo dedicado a funciones secundarias.

|Columna|DESCRIPCIÓN|
|------------|-----------------|
|**Tiempo inclusivo de aplicación**|El tiempo inclusivo de aplicación total de todas las llamadas a esta función.|
|**Porcentaje de tiempo inclusivo de aplicación**|El porcentaje de tiempo inclusivo transcurrido total de la ejecución de generación de perfiles que se ha empleado en el tiempo inclusivo de aplicación total de esta función.|
|**Promedio de tiempo inclusivo de aplicación**|El promedio de tiempo inclusivo de aplicación de una llamada a esta función.|
|**Tiempo inclusivo máximo de aplicación**|El tiempo inclusivo de aplicación máximo de una llamada a esta función.|
|**Tiempo inclusivo mínimo de aplicación**|El tiempo inclusivo de aplicación mínimo de una llamada a esta función.|

## <a name="application-exclusive-values"></a>Valores de tiempo exclusivo de aplicación
 Los valores exclusivos de aplicación indican el tiempo que una función se estaba ejecutando directamente en la parte superior de la pila de llamadas. No incluye el tiempo dedicado a llamadas al sistema operativo, como modificadores de contexto y operaciones de E/S, ni incluye el tiempo dedicado a funciones secundarias.

|Columna|DESCRIPCIÓN|
|------------|-----------------|
|**Tiempo exclusivo de aplicación**|El tiempo exclusivo de aplicación total de todas las llamadas a esta función.|
|**Porcentaje de tiempo exclusivo de aplicación**|El porcentaje de tiempo exclusivo transcurrido total de la ejecución de generación de perfiles que se ha empleado en el tiempo exclusivo de aplicación total de esta función.|
|**Promedio de tiempo exclusivo de aplicación**|El promedio de tiempo exclusivo de aplicación de una llamada a esta función.|
|**Tiempo exclusivo de aplicación máximo**|El tiempo exclusivo de aplicación máximo de una llamada a esta función.|
|**Tiempo exclusivo mínimo de aplicación**|El tiempo exclusivo de aplicación mínimo de una llamada a esta función.|

## <a name="see-also"></a>Vea también
- [Cómo: Personalizar las columnas de la vista de informes](../profiling/how-to-customize-report-view-columns.md)
- [Vista Funciones: muestreo](../profiling/functions-view-dotnet-memory-sampling-data.md)
- [Vista Funciones](../profiling/functions-view-instrumentation-data.md)
- [Vista Funciones](../profiling/functions-view-sampling-data.md)
