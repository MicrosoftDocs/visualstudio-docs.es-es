---
title: "Vista de resumen: datos de instrumentaci&#243;n del generador de perfiles | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Vista Resumen"
ms.assetid: 0a3b3a1f-e22b-4ac8-b46e-71694e9b2cf1
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Vista de resumen: datos de instrumentaci&#243;n del generador de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vista Resumen muestra información sobre las funciones con mayor incidencia en el rendimiento de una ejecución de generación de perfiles.  Para obtener más información, incluida una descripción de las listas de Vínculos de notificaciones y de Informes, vea [Vista Resumen](../profiling/summary-view.md).  
  
## Gráfico de escala de tiempo  
 El gráfico de escala de tiempo de la vista de resumen muestra la utilización del procesador \(CPU\) por parte de la aplicación perfilada durante el tiempo en que se produjo la generación de perfiles.  Puede usar el gráfico de escala de tiempo para filtrar la vista en función de un intervalo de tiempo seleccionado.  Para obtener más información, vea [Cómo: Filtrar vistas de informe desde la escala de tiempo de resumen](../Topic/How%20to:%20Filter%20Report%20Views%20from%20the%20Summary%20Timeline.md).  
  
## Ruta de acceso activa  
 La **Ruta de acceso activa** muestra la ruta de acceso de ejecución que consumió más tiempo.  Puede hacer clic en una función para mostrar la vista Detalles de la función correspondiente.  Para mostrar otras vistas de la función, haga clic con el botón secundario del mouse en la función y, a continuación, haga clic en una vista de la lista.  
  
 La **Ruta de acceso activa** incluye los datos siguientes para cada función:  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Name**|Nombre de la función.|  
|**% de tiempo inclusivo transcurrido**|El porcentaje de tiempo que la función dedicó a ejecutar código de su cuerpo de función y de las funciones a las que llamó con respecto al tiempo total de los datos de generación de perfiles.|  
|**% de tiempo exclusivo transcurrido**|El porcentaje de tiempo que la función dedicó a ejecutar código de su cuerpo de función con respecto al tiempo total de los datos de generación de perfiles.  No se incluye el tiempo dedicado a las funciones a las que llamó la función.|  
  
## Funciones con la mayor parte del trabajo individual  
 Una lista de las funciones que utilizaron la mayor parte del tiempo ejecutando código del cuerpo de la función y no en funciones a las que llamaron.  
  
 **Funciones con la mayor parte del trabajo individual** incluye los datos siguientes para cada función:  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Name**|Nombre de la función.|  
|**% de tiempo de exclusión**|El porcentaje de tiempo que la función dedicó a ejecutar código de su cuerpo de función con respecto al tiempo total de los datos de generación de perfiles.  No se incluye el tiempo dedicado a las funciones a las que llamó la función.|  
  
## Vea también  
 [Vista Resumen](../profiling/summary-view-sampling-data.md)   
 [Vista Resumen](../profiling/summary-view-dotnet-memory-data.md)