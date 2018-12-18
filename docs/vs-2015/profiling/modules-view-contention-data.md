---
title: 'Vista Módulos: datos de contención | Microsoft Docs'
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
- Modules view
ms.assetid: 1a9aa122-2d8f-4a09-b503-92975aa6b648
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9c98689007a9497a4186dc19086ec46588b0a842
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51759406"
---
# <a name="modules-view---contention-data"></a>Vista Módulos: datos de contención
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En la vista Módulos de datos de contención se muestran datos de simultaneidad agrupados por los módulos de los que se toman muestras en los datos de generación de perfiles. Cada módulo es la raíz de un árbol jerárquico. Las funciones del módulo en el que se produjeron los eventos de contención se muestran debajo del nodo de módulo.  
  
 Si la función estaba ejecutando su propio código cuando se produjo un evento de contención, es decir, si la función estaba en la parte superior de la pila de llamadas, las líneas de código fuente y las direcciones de instrucción que se estaban ejecutando aparecen debajo del nodo de función. Dado que cuando se ejecuta la línea o la instrucción, se recopilan datos de una línea de código fuente o un puntero de instrucción, los valores inclusivos y exclusivos siempre son los mismos para los datos de línea y de instrucción.  
  
 En la tabla siguiente se describen los valores de las columnas de la vista Módulos de datos de contención.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Tiempo de bloqueo exclusivo**|-   Para una función, el tiempo durante el cual esta función no ha podido ejecutar código en el cuerpo de la función. No se incluye el tiempo de bloqueo de las funciones a las que llamó la función.<br />-   Para un módulo, la suma de tiempo de bloqueo exclusivo de las funciones del módulo.<br />-   Para una línea o una instrucción, el tiempo durante el que dicha línea o instrucción no ha podido ejecutarse.|  
|**Porcentaje de tiempo de bloqueo exclusivo**|-   Para una función o un módulo, el porcentaje de tiempo de bloqueo exclusivo de esta función o módulo con respecto al tiempo de bloqueo total de la ejecución de generación de perfiles.<br />-   Para una línea o una instrucción, el porcentaje del tiempo de bloqueo total de la ejecución de generación de perfiles durante el que dicha línea o instrucción no ha podido ejecutarse.|  
|**Contenciones exclusivas**|-   Para una función, el número de veces en las que esta función no ha podido ejecutar código en el cuerpo de la función. No se incluyen las contenciones en las funciones a las que ha llamado la función.<br />-   Para un módulo, la suma de las contenciones exclusivas de las funciones del módulo.<br />-   Para una línea o una instrucción, el número de veces en las que dicha línea o instrucción no ha podido ejecutarse.|  
|**Porcentaje de contenciones exclusivas**|-   Para una función o un módulo, el porcentaje de todas las contenciones de la ejecución de generación de perfiles que han sido contenciones exclusivas de esta función o módulo.<br />-   Para una línea o una instrucción, el porcentaje de todas las contenciones de la ejecución de generación de perfiles que han impedido que dicha línea o instrucción se ejecutara.|  
|**Tiempo de bloqueo inclusivo**|-   Para una función, el tiempo durante el que esta función, o una función a la que ha llamado esta función, no ha podido ejecutarse.<br />-   Para un módulo, la suma de tiempo de bloqueo durante el que al menos una función de este módulo ha estado en la pila.<br />-   Para una línea o una instrucción, el tiempo durante el que dicha línea o instrucción no ha podido ejecutarse.|  
|**Porcentaje de tiempo de bloqueo inclusivo**|-   Para una función o un módulo, el porcentaje de tiempo de bloqueo inclusivo de esta función o módulo con respecto al tiempo de bloqueo total de la ejecución de generación de perfiles.<br />-   Para una línea o una instrucción, el porcentaje del tiempo de bloqueo total de la ejecución de generación de perfiles durante el que dicha línea o instrucción se estaba ejecutando.|  
|**Contenciones inclusivas**|-   Para una función, el número de veces que esta función, o una función a la que ha llamado esta función, no ha podido ejecutarse.<br />-   Para un módulo, el número de contenciones en las que al menos una función de este módulo ha estado en la pila.<br />-   Para una línea o una instrucción, el número de veces en las que dicha línea o instrucción no ha podido ejecutarse.|  
|**Porcentaje de contenciones inclusivas**|-   Para una función o un módulo, el porcentaje de todas las contenciones de la ejecución de generación de perfiles que han sido contenciones inclusivas de esta función o módulo.<br />-   Para una línea o una instrucción, el porcentaje del tiempo de bloqueo total de la ejecución de generación de perfiles durante el que dicha línea o instrucción se estaba ejecutando.|  
|**Número de línea de la función**|Número de línea del inicio de esta función en el archivo de origen.|  
|**Nombre del módulo**|Nombre del módulo que contiene la función, línea o dirección del puntero de instrucción.|  
|**Ruta de acceso del módulo**|La ruta de acceso del módulo que contiene el módulo, función, línea o dirección del puntero de instrucción.|  
|**Name**|Nombre del módulo o de la función.|  
|**Identificador del proceso**|Identificador de proceso (PID) de la ejecución de generación de perfiles.|  
|**Nombre de proceso**|Nombre del proceso.|  
|**Archivo de código fuente**|Archivo de origen que contiene la definición de esta función.|  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Personalizar las columnas de la vista de informes](../profiling/how-to-customize-report-view-columns.md)   
 [Vista Módulos](../profiling/modules-view.md)   
 [Vista Módulos: instrumentación](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Vista Módulos: muestreo](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [Vista Módulos](../profiling/modules-view-instrumentation-data.md)   
 [Vista Módulos](../profiling/modules-view-sampling-data.md)



