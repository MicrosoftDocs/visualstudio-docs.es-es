---
title: 'Vista Resumen: datos de instrumentación | Microsoft Docs'
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
- Summary view
ms.assetid: 0a3b3a1f-e22b-4ac8-b46e-71694e9b2cf1
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 17534c0c7970238d4b6ef3de79c87d637743ff83
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47565978"
---
# <a name="summary-view---instrumentation-data"></a>Vista Resumen: datos de instrumentación
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [vista Resumen: datos de instrumentación](https://docs.microsoft.com/visualstudio/profiling/summary-view-instrumentation-data).  
  
La vista Resumen muestra información acerca de las funciones más exigentes en una generación de perfiles. Para obtener más información, incluyendo una descripción de los vínculos de notificación y las listas de informes, consulte [Vista Resumen](../profiling/summary-view.md).  
  
## <a name="timeline-graph"></a>Gráfico de escala de tiempo  
 El gráfico de escala de tiempo en la vista Resumen muestra la utilización del procesador (CPU) por la aplicación de la que se generan perfiles durante el tiempo que se generaron perfiles. Puede usar el gráfico de escala de tiempo para filtrar la vista en un intervalo de tiempo seleccionado. Para obtener más información, consulte [Cómo: Filtrar vistas de informe desde la escala de tiempo de resumen](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
## <a name="hot-path"></a>Ruta de acceso activa  
 La **Ruta de acceso activa** muestra la ruta de acceso de ejecución que consumió más tiempo. Puede hacer clic en una función para mostrar la vista Detalles de la misma. Para mostrar otras vistas para la función haga clic con el botón derecho en ella y después haga clic en una vista de la lista.  
  
 La **Ruta de acceso activa** incluye los siguientes datos para cada función:  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Name**|Nombre de la función.|  
|**Porcentaje de tiempo inclusivo transcurrido**|El porcentaje del tiempo total de los datos de generación de perfiles que la función dedicó a ejecutar código en el cuerpo de la función y en funciones a las que llamó.|  
|**Porcentaje de tiempo exclusivo transcurrido**|El porcentaje del tiempo total de los datos de generación de perfiles que la función dedicó a ejecutar código en el cuerpo de la función. No se incluye el tiempo dedicado a funciones a las que llamó la función.|  
  
## <a name="functions-with-most-individual-work"></a>Funciones que realizan la mayor parte de trabajo individual  
 Una lista de las funciones que consumieron más tiempo ejecutando código en el cuerpo de la función y no en funciones a las que llamó.  
  
 **Funciones que realizan la mayor parte de trabajo individual** incluye los siguientes datos para cada función:  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Name**|Nombre de la función.|  
|**Porcentaje de tiempo exclusivo**|El porcentaje del tiempo total de los datos de generación de perfiles que la función dedicó a ejecutar código en el cuerpo de la función. No se incluye el tiempo dedicado a funciones a las que llamó la función.|  
  
## <a name="see-also"></a>Vea también  
 [Vista Resumen](../profiling/summary-view-sampling-data.md)   
 [Vista Resumen](../profiling/summary-view-dotnet-memory-data.md)



