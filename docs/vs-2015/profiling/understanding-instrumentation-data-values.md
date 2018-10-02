---
title: Introducción a los valores de datos de instrumentación | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Profiling Tools,instrumentation
- instrumentation profiling method
ms.assetid: 2cf94cf9-c317-4a52-bf00-670f1262165e
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da7a4ddebb8504d4a6ac9b3d39a0ee4646f5d8f5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47580460"
---
# <a name="understanding-instrumentation-data-values"></a>Introducción a los valores de datos de instrumentación
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [los valores de datos de instrumentación de comprensión](https://docs.microsoft.com/visualstudio/profiling/understanding-instrumentation-data-values).  
  
El método de generación de perfiles *Instrumentación* del [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] registra información de tiempos detallada de llamadas a funciones, líneas y las instrucciones de la aplicación perfilada  
  
 **Requisitos**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
 El método de instrumentación inserta código al principio y al final de las funciones de destino en el binario del que se generan perfiles, y antes y después de cada llamada realizada por esas funciones a otras funciones. El código insertado registra lo siguiente:  
  
-   El intervalo entre este evento de recopilación y el anterior.  
  
-   Si el sistema operativo ha realizado una operación durante el intervalo. Por ejemplo, el sistema operativo puede leer o escribir en disco, o cambiar entre el subproceso de destino y un subproceso de otro proceso.  
  
 **Requisitos**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
 Para cada intervalo, el análisis del generador de perfiles reconstruye la pila de llamadas que estaba presente al final del intervalo. Una pila de llamadas es la lista de funciones que están activas en un procesador en un momento dado. Solo una función (la función actual) está ejecutando código, las demás funciones forman la cadena de llamadas de función que dan como resultado la llamada a la función actual (la pila de llamadas).  
  
 Para cada función en la pila de llamadas cuando se registró el intervalo, el análisis del generador de perfiles agrega el intervalo a uno o más valores de entre cuatro valores de datos posibles para la función. El análisis agrega el intervalo a un valor de datos para una función basándose en dos criterios:  
  
-   Si el intervalo se produjo en el código de la función o en una *función secundaria* (una función que llamó a la función).  
  
-   Si se produjo un evento de sistema operativo en el intervalo.  
  
 Los valores de datos para un intervalo de una función o rango de datos se denominan *Tiempo inclusivo transcurrido*, *Tiempo exclusivo transcurrido*, *Tiempo inclusivo de aplicación* y *Tiempo exclusivo de aplicación*:  
  
-   Todos los intervalos de una función se agregan al valor de datos Tiempo inclusivo transcurrido.  
  
-   Si el intervalo se produjo en el código de la función y no en una función secundaria, el intervalo se agrega al valor de datos Tiempo exclusivo transcurrido de la función.  
  
-   Si no se ha producido un evento de sistema operativo en el intervalo, el intervalo se agrega al valor de datos Tiempo inclusivo de aplicación.  
  
-   Si no se ha producido un evento de sistema operativo en el intervalo y el intervalo se produjo en la ejecución directa del código de función (es decir, no tuvo lugar en una función secundaria), el intervalo se agrega al valor de datos Tiempo exclusivo de aplicación.  
  
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
 [Analizar datos de herramientas de rendimiento](../profiling/analyzing-performance-tools-data.md)   
 [Cómo: Elegir métodos de recopilación](../profiling/how-to-choose-collection-methods.md)



