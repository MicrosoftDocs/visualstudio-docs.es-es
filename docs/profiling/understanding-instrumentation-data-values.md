---
title: Introducción a los valores de datos de instrumentación | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,instrumentation
- instrumentation profiling method
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 524f6f575725fed754c3873af8a9ff62a3c3686f
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2018
ms.locfileid: "34477553"
---
# <a name="understand-instrumentation-data-values"></a>Introducción a los valores de datos de instrumentación

El método de generación de perfiles *Instrumentación* de Visual Studio registra información de tiempos detallada de llamadas a funciones, líneas y las instrucciones de la aplicación perfilada

El método de instrumentación inserta código al principio y al final de las funciones de destino en el binario del que se generan perfiles, y antes y después de cada llamada realizada por esas funciones a otras funciones. El código insertado registra la información siguiente:

- El intervalo entre este evento de recopilación y el anterior.

- Si el sistema operativo ha realizado una operación durante el intervalo. Por ejemplo, el sistema operativo puede leer o escribir en disco, o cambiar entre el subproceso de destino y un subproceso de otro proceso.

Para cada intervalo, el análisis del generador de perfiles reconstruye la pila de llamadas que estaba presente al final del intervalo. Una pila de llamadas es la lista de funciones que están activas en un procesador en un momento dado. Solo una función (la función actual) está ejecutando código, las demás funciones forman la cadena de llamadas de función que dan como resultado la llamada a la función actual (la pila de llamadas).

Para cada función en la pila de llamadas cuando se registró el intervalo, el análisis del generador de perfiles agrega el intervalo a uno o más valores de entre cuatro valores de datos posibles para la función. El análisis agrega el intervalo a un valor de datos para una función basándose en dos criterios:

- Si el intervalo se produjo en el código de la función o en una *función secundaria* (una función que llamó a la función).

- Si se produjo un evento de sistema operativo en el intervalo.

Los valores de datos para un intervalo de una función o rango de datos se denominan *Tiempo inclusivo transcurrido*, *Tiempo exclusivo transcurrido*, *Tiempo inclusivo de aplicación* y *Tiempo exclusivo de aplicación*:

- Todos los intervalos de una función se agregan al valor de datos Tiempo inclusivo transcurrido.

- Si el intervalo se produjo en el código de la función y no en una función secundaria, el intervalo se agrega al valor de datos Tiempo exclusivo transcurrido de la función.

- Si no se ha producido un evento de sistema operativo en el intervalo, el intervalo se agrega al valor de datos Tiempo inclusivo de aplicación.

- Si no se ha producido un evento de sistema operativo en el intervalo y el intervalo se produjo en la ejecución directa del código de función (es decir, no tuvo lugar en una función secundaria), el intervalo se agrega al valor de datos Tiempo exclusivo de aplicación.

Los informes de las herramientas de generación de perfiles agregan los valores totales de las funciones de la sesión de generación de perfiles y los procesos, subprocesos y binarios de la sesión.

## <a name="elapsed-inclusive-values"></a>Valores de Tiempo inclusivo transcurrido

El tiempo total dedicado a ejecutar una función y sus funciones secundarias.

Los valores de Tiempo inclusivo transcurrido incluyen los intervalos dedicados a ejecutar directamente el código de función y los intervalos dedicados a ejecutar las funciones secundarias de la función de destino. Los intervalos de la función o sus funciones secundarias que incluyen la espera por el sistema operativo también se incluyen en los valores de Tiempo inclusivo transcurrido.

## <a name="elapsed-exclusive-values"></a>Valores de Tiempo exclusivo transcurrido

El tiempo dedicado a ejecutar una función, excluyendo el tiempo dedicado a funciones secundarias.

Los valores de Tiempo exclusivo transcurrido incluyen los intervalos dedicados a ejecutar directamente el código de función, independientemente de si se produjo un evento del sistema operativo en el intervalo. No se incluyen los intervalos dedicados a funciones secundarias llamadas por la función de destino en los valores Tempo exclusivo transcurrido.

## <a name="application-inclusive-values"></a>Valores de Tiempo inclusivo de aplicación

El tiempo dedicado a ejecutar una función y sus funciones secundarias, excluyendo el tiempo dedicado a eventos del sistema operativo.

Los valores de tiempo inclusivo de aplicación no incluyen los intervalos que contienen eventos del sistema operativo. Dichos valores incluyen todos los otros intervalos que se han dedicado a ejecutar una función, independientemente de si el intervalo se dedicó a ejecutar directamente el código de función o a funciones secundarias de la función de destino.

## <a name="application-exclusive-values"></a>Valores de Tiempo exclusivo de aplicación

El tiempo dedicado a ejecutar una función, excluyendo el tiempo dedicado a funciones secundarias y a eventos del sistema operativo.

Dichos valores no incluyen los intervalos que contienen eventos del sistema operativo o intervalos dedicados a ejecutar funciones llamadas por la función. Los valores de tiempo exclusivo de aplicación incluyen solo los intervalos dedicados a ejecutar directamente el código de función y que no contienen un evento de sistema operativo.

## <a name="elapsed-inclusive-percent"></a>Porcentaje de tiempo inclusivo transcurrido

El porcentaje de los valores de tiempo inclusivo transcurrido total de la sesión de generación de perfiles que eran valores de tiempo inclusivo transcurrido de la función, el módulo, el subproceso o el proceso.

100 * tiempo inclusivo transcurrido de función / tiempo inclusivo transcurrido de sesión

## <a name="elapsed-exclusive-percent"></a>Porcentaje de tiempo exclusivo transcurrido

El porcentaje de los valores de tiempo inclusivo transcurrido total de la sesión de generación de perfiles que eran valores de tiempo exclusivo transcurrido de la función, el módulo, el subproceso o el proceso.

100 * tiempo exclusivo transcurrido de función / tiempo inclusivo transcurrido de sesión

## <a name="application-inclusive-percent"></a>Porcentaje de tiempo inclusivo de aplicación

El porcentaje de los valores de tiempo inclusivo de aplicación total de la sesión de generación de perfiles que eran valores de tiempo inclusivo de aplicación de la función, el módulo, el subproceso o el proceso.

100 * tiempo inclusivo de aplicación de función / tiempo inclusivo de aplicación de sesión

## <a name="application-exclusive-percent"></a>Porcentaje de tiempo exclusivo de aplicación

El porcentaje de los valores de tiempo inclusivo de aplicación total de la sesión de generación de perfiles que eran intervalos de tiempo exclusivo de aplicación de la función, el módulo, el subproceso o el proceso.

100 * tiempo exclusivo de aplicación de función / tiempo inclusivo de aplicación de sesión

## <a name="see-also"></a>Vea también

[Análisis de datos de herramientas de rendimiento](../profiling/analyzing-performance-tools-data.md)  
[Elección de métodos de recopilación](../profiling/how-to-choose-collection-methods.md)