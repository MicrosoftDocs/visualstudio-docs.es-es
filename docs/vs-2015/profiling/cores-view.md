---
title: Vista Núcleos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.cores
helpviewer_keywords:
- Concurrency Visualizer, Cores View
ms.assetid: e47af672-9785-4899-bd45-4d9dda3c396f
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 869980fe7bbb773d566dffd38088b003e3a97a3d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145642"
---
# <a name="cores-view"></a>Vista de núcleos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En la vista Núcleos se muestra cómo se asignó la ejecución de subprocesos a los núcleos de procesadores lógicos. Si está escribiendo aplicaciones de servidor, esta vista puede ayudarlo a optimizar el rendimiento de la memoria caché mediante el uso de administración de grupos de subprocesos o de afinidad de subprocesos. También puede ayudarlo a examinar los casos en que el uso de la afinidad de subprocesos puede haber empeorado el problema de la migración entre núcleos. La vista Núcleos tiene dos partes: un gráfico y una leyenda.  
  
 El gráfico muestra los núcleos lógicos en el eje Y y el tiempo en el eje X. Cada subproceso del gráfico tiene un color único para que pueda seguir su movimiento entre núcleos a lo largo del tiempo. Puede filtrar los subprocesos de este gráfico si los selecciona en el área de la leyenda.  
  
 El área de la leyenda tiene una entrada para cada color del gráfico. Cada entrada muestra el color y el nombre del subproceso, el número de cambios de contexto entre núcleos, el número total de cambios de contexto y el porcentaje de cambios de contexto que atraviesan núcleos. La leyenda se ordena por el número de cambios de contexto entre núcleos, en orden decreciente. Enumera únicamente los subprocesos ejecutados durante el intervalo de tiempo mostrado.  La lista se actualiza si hace zoom o un movimiento panorámico.  
  
## <a name="see-also"></a>Consulte también  
 [Visualizador de simultaneidad](../profiling/concurrency-visualizer.md)   
 [Vista de utilización](../profiling/utilization-view.md)   
 [Vista Subprocesos](../profiling/threads-view-parallel-performance.md)
