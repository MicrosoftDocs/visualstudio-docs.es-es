---
title: 'Vista Llamador y destinatario: datos de contención | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Caller/Callee view
ms.assetid: a18a1b1b-9b39-43c7-b1f3-708fd20376f6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: db4b0bf6e29be1607fcf05557c8089074efa9f78
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53902911"
---
# <a name="callercallee-view----contention-data"></a>Vista Llamador y destinatario: datos de contención
La vista Llamador y destinatario muestra información de contención para una función seleccionada y sus funciones primarias y secundarias. La vista Llamador y destinatario contiene tres cuadrículas.  
  
 **Función actual** se muestra en la cuadrícula central e incluye información sobre la contención para la función seleccionada. Los valores incluyen todas las contenciones de bloqueo para la función.  
  
 **Funciones que llamaron a la función actual** se muestra en la cuadrícula superior e incluye las contribuciones individuales de las funciones de llamador (primarias) a los valores de la función seleccionada (actual).  
  
 **Funciones llamadas por la función actual** se muestra en la cuadrícula inferior e incluye información de contención para las funciones de destinatario (secundarias) de la función seleccionada cuando la función actual llamó a la función secundaria.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Type**|El contexto de la función:<br /><br /> -   **0**: la función actual<br />-   **1**: una función que llama a la función actual<br />-   **2**: una función llamada por la función actual<br /><br /> Solo disponible en los informes de línea de comandos de [VSPerfReport](../profiling/vsperfreport.md).|  
|**Tiempo de bloqueo exclusivo**|-En la función actual, el tiempo durante el cual esta función no pudo ejecutar código en el cuerpo de la función. No se incluye el tiempo de bloqueo de las funciones a las que llamó la función.<br />- En una función de llamador, la parte del tiempo de bloqueo exclusivo de la función actual que transcurrió cuando esta función llamó a la función actual.<br />-En una función de destinatario, el tiempo durante el cual esta función no pudo ejecutar su propio código cuando la función actual llamó a esta función. No se incluye el tiempo de bloqueo de las funciones secundarias a las que llamó la función de destinatario.|  
|**Porcentaje de tiempo de bloqueo exclusivo**|El porcentaje de tiempo de bloqueo exclusivo de esta función en este contexto con respecto al tiempo de bloqueo total de la ejecución de generación de perfiles.|  
|**Contenciones exclusivas**|- En la función actual, el número de veces en las que esta función no pudo ejecutar código en el cuerpo de la función. Las contenciones que se produjeron en funciones a las que llamó la función no se incluyen.<br />- En una función de llamador, el número de contenciones exclusivas de la función actual que se produjeron cuando esta función llamó a la función actual.<br />- En la función de destinatario, el número de veces en las que esta función no pudo ejecutar código en el cuerpo de la función cuando la función actual llamó a esta función. Las contenciones que se produjeron en funciones a las que llamó la función de destinatario no se incluyen.|  
|**Porcentaje de contenciones exclusivas**|El porcentaje de contenciones exclusivas de esta función en este contexto con respecto a todas las contenciones en la ejecución de generación de perfiles.|  
|**Dirección de la función**|La dirección o el token de la función.|  
|**Nombre de la función**|El nombre completo de la función.|  
|**Tiempo de bloqueo inclusivo**|- En la función actual, el tiempo durante el cual no se pudo ejecutar esta función o una de las funciones a las que llamó esta función. Se incluye el tiempo de bloqueo de las funciones a las que llamó la función actual.<br />- En una función de llamador, la parte del tiempo de bloqueo inclusivo de la función actual que transcurrió cuando esta función llamó a la función actual.<br />- En una función de destinatario, el tiempo durante el cual no se pudo ejecutar esta función o una de las funciones a las que llamó la función cuando la función actual llamó a esta función. Se incluye el tiempo de bloqueo de las funciones a las que llamó la función de destinatario.|  
|**Porcentaje de tiempo de bloqueo inclusivo**|El porcentaje de tiempo de bloqueo inclusivo de esta función en este contexto con respecto al tiempo de bloqueo total de la ejecución de generación de perfiles.|  
|**Contenciones inclusivas**|- En la función actual, el número de veces que no se pudo ejecutar esta función o una de las funciones a las que llamó esta función. Se incluyen las contenciones que se produjeron en las funciones a las que llamó la función.<br />- En una función de llamador, el número de contenciones inclusivas de la función actual que se produjeron cuando esta función llamó a la función actual.<br />- En una función de destinatario, el número de veces que no se pudo ejecutar esta función o una de las funciones a las que llamó la función cuando la función actual llamó a esta función. Se incluyen las contenciones que se produjeron en funciones a las que llamó la función de destinatario.|  
|**Porcentaje de contenciones inclusivas**|El porcentaje de contenciones exclusivas de esta función en este contexto con respecto a todas las contenciones en la ejecución de generación de perfiles.|  
|**Número de línea de la función**|Número de línea del inicio de esta función en el archivo de origen.|  
|**Nombre del módulo**|Nombre del módulo que contiene la función.|  
|**Ruta de acceso del módulo**|Ruta de acceso del módulo que contiene la función.|  
|**Identificador del proceso**|El identificador de proceso (PID) en el que se produjeron las contenciones.|  
|**Nombre de proceso**|Nombre del proceso.|  
|**Nombre de la función raíz**|El nombre de la función actual. Solo disponible en los informes de línea de comandos de [VSPerfReport](../profiling/vsperfreport.md).|  
|**Archivo de código fuente**|Archivo de origen que contiene la definición de esta función.|  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Personalizar las columnas de la vista de informes](../profiling/how-to-customize-report-view-columns.md)   
 [Vista Llamador y destinatario](../profiling/caller-callee-view.md)   
 [Vista Llamador y destinatario: datos de muestreo](../profiling/caller-callee-view-sampling-data.md)   
 [Vista Llamador y destinatario: datos de instrumentación de memoria de .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Vista Llamador y destinatario: datos de muestreo de memoria de .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Vista Llamador y destinatario: datos de instrumentación](../profiling/caller-callee-view-instrumentation-data.md)