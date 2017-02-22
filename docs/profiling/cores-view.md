---
title: "Vista de n&#250;cleos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.cores"
helpviewer_keywords: 
  - "Visualizador de simultaneidad, vista de núcleos"
ms.assetid: e47af672-9785-4899-bd45-4d9dda3c396f
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Vista de n&#250;cleos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vista de núcleos muestra cómo se asignó la ejecución de subprocesos a los núcleos del procesador.  Si está escribiendo aplicaciones de servidor, esta vista puede ayudarle a optimizar el rendimiento de la memoria caché utilizando la afinidad de subprocesos o la administración del grupo de subprocesos.  También puede ayudarle a examinar los casos donde el uso de la afinidad de subprocesos pueda haber empeorado el problema de la migración entre núcleos.  La vista de núcleos tiene dos partes, un gráfico y una leyenda.  
  
 El gráfico muestra los núcleos lógicos en el eje Y y el tiempo en el eje X.  Cada subproceso del gráfico tiene un color único para que pueda seguir el movimiento de cada subproceso por los núcleos a lo largo del tiempo.  Puede filtrar los subprocesos en este gráfico seleccionándolos en el área de la leyenda.  
  
 El área de la leyenda tiene una entrada para cada color en el gráfico.  Muestra el color y el nombre del subproceso, el recuento de cambios de contexto entre núcleos, el número total de cambios de contexto y el porcentaje de cambios de contexto entre núcleos.  La leyenda se ordena por el número de cambios de contexto entre núcleos, en orden descendente.  Enumera sólo los subprocesos que se ejecutaron durante el intervalo temporal mostrado.  La lista se actualiza si se realiza un acercamiento o alejamiento.  
  
## Vea también  
 [Visualizador de simultaneidad](../profiling/concurrency-visualizer.md)   
 [Vista de utilización](../profiling/utilization-view.md)   
 [Vista de subprocesos](../profiling/threads-view-parallel-performance.md)