---
title: "Vista de resumen: datos de memoria de .NET del generador de perfiles | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Vista Resumen"
ms.assetid: 0cb317c3-0ae6-4531-aaa8-447576eec037
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Vista de resumen: datos de memoria de .NET del generador de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vista de resumen muestra información sobre las funciones y los tipos de .NET asignaron la mayoría de la memoria y sobre los tipos que se crearon la mayoría de las veces en una ejecución de generación de perfiles.  Para obtener más información, incluida una descripción de las listas de Vínculos de notificaciones y de Informes, vea [Vista Resumen](../profiling/summary-view.md).  
  
## Gráfico de escala de tiempo  
 El gráfico de escala de tiempo de la vista de resumen muestra la utilización del procesador \(CPU\) por parte de la aplicación perfilada durante el tiempo en que se produjo la generación de perfiles.  Puede usar el gráfico de escala de tiempo para filtrar la vista en función de un intervalo de tiempo seleccionado.  Para obtener más información, vea [Cómo: Filtrar vistas de informe desde la escala de tiempo de resumen](../Topic/How%20to:%20Filter%20Report%20Views%20from%20the%20Summary%20Timeline.md).  
  
## Funciones que asignan la mayoría de la memoria  
 Enumera las funciones que asignaron el mayor número de bytes de memoria en la ejecución de generación de perfiles.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Name**|Nombre de la función.|  
|**% de bytes**|Porcentaje de bytes asignados por esta función o por una función secundaria llamada por esta función con respecto a todos los bytes asignados en la ejecución de generación de perfiles.|  
  
## Tipos con la mayoría de la memoria asignada  
 Enumera los tipos para los que se asignó el mayor número de bytes de memoria en la ejecución de generación de perfiles.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Name**|Nombre del tipo.|  
|**% de bytes**|Porcentaje de bytes asignados a este tipo con respecto a todos los bytes asignados durante la generación de perfiles.|  
  
## Tipos con la mayoría de las instancias  
 Enumera los tipos creados la mayoría de las veces durante la ejecución de generación de perfiles. tenía  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Name**|Nombre del tipo.|  
|**% de instancias**|Porcentaje del número total de objetos .NET creados durante la generación de perfiles que fueron instancias de este tipo.|  
  
## Vea también  
 [Vista Resumen](../profiling/summary-view-sampling-data.md)   
 [Vista Resumen](../profiling/summary-view-instrumentation-data.md)