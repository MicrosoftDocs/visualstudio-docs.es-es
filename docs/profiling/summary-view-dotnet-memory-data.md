---
title: 'Vista Resumen: datos de memoria de .NET | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Summary view
ms.assetid: 0cb317c3-0ae6-4531-aaa8-447576eec037
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 174f8612dd4f0678d8bbdc8be5c6a9b37cfc8b61
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="summary-view---net-memory-data"></a>Vista Resumen: datos de memoria de .NET
La vista Resumen muestra información sobre las funciones de .NET y los tipos que asignaron la mayor cantidad de memoria, y los tipos que se crearon la mayoría de las veces en un proceso de generación de perfiles. Para obtener más información, incluyendo una descripción de los vínculos de notificación y las listas de informes, consulte [Vista Resumen](../profiling/summary-view.md).  
  
## <a name="timeline-graph"></a>Gráfico de escala de tiempo  
 El gráfico de escala de tiempo en la vista Resumen muestra la utilización del procesador (CPU) por la aplicación de la que se generan perfiles durante el tiempo que se generaron perfiles. Puede usar el gráfico de escala de tiempo para filtrar la vista en un intervalo de tiempo seleccionado. Para obtener más información, consulte [Cómo: Filtrar vistas de informe desde la escala de tiempo de resumen](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
## <a name="functions-allocating-most-memory"></a>Funciones que asignan la mayoría de la memoria  
 Enumera las funciones que asignaron el mayor número de bytes de memoria en la generación de perfiles.  
  
|Columna|Description|  
|------------|-----------------|  
|**Name**|Nombre de la función.|  
|**Porcentaje de bytes**|El porcentaje de todos los bytes asignados en la generación de perfiles que fueron asignados por esta función o una función secundaria a la que llamó esta función.|  
  
## <a name="types-with-most-memory-allocated"></a>Tipos con más memoria asignada  
 Enumera los tipos para los que se asignó el mayor número de bytes de memoria en la generación de perfiles.  
  
|Columna|Description|  
|------------|-----------------|  
|**Name**|Nombre del tipo.|  
|**Porcentaje de bytes**|El porcentaje de todos los bytes asignados en la generación de perfiles que se asignaron para este tipo.|  
  
## <a name="types-with-most-instances"></a>Tipos con más instancias  
 Enumera los tipos que se crearon más veces durante la generación de perfiles. tenía  
  
|Columna|Description|  
|------------|-----------------|  
|**Name**|Nombre del tipo.|  
|**Porcentaje de instancias**|Porcentaje del número total de objetos .NET creados en la ejecución de generación de perfiles que eran instancias de este tipo.|  
  
## <a name="see-also"></a>Vea también  
 [Vista Resumen](../profiling/summary-view-sampling-data.md)   
 [Vista Resumen](../profiling/summary-view-instrumentation-data.md)