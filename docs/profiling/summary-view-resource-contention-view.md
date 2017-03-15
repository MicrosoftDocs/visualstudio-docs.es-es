---
title: "Vista de resumen: vista de contenci&#243;n de recursos del generador de perfiles | Microsoft Docs"
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
ms.assetid: 6da57b83-7b42-4d7c-9aea-8e0a830faf6b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Vista de resumen: vista de contenci&#243;n de recursos del generador de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vista de resumen muestra información sobre los eventos de la aplicación en que se suspendió un subproceso o proceso mientras esperaba el acceso a un recurso.  
  
 Para obtener más información, incluida una descripción de las listas de Vínculos de notificaciones y de Informes, vea [Vista Resumen](../profiling/summary-view.md).  
  
## Gráfico de escala de tiempo  
 El gráfico de escala de tiempo de la vista de resumen muestra el número de eventos de contención de la aplicación perfilada durante el tiempo en que se produjo la generación de perfiles.  Puede usar el gráfico de escala de tiempo para filtrar la vista en función de un intervalo de tiempo seleccionado.  Para obtener más información, vea [Cómo: Filtrar vistas de informe desde la escala de tiempo de resumen](../Topic/How%20to:%20Filter%20Report%20Views%20from%20the%20Summary%20Timeline.md).  
  
## Recursos más contenidos  
 **Recursos más contenidos** enumera los recursos de la aplicación que produjeron la mayoría de los eventos de contención.  Puede hacer clic en un nombre de recurso para mostrar la vista Contenciones.  Esta vista proporciona una escala de tiempo detallada de las contenciones de recurso por subproceso.  
  
 **Recursos más contenidos** incluye los siguientes datos de cada recurso.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Name**|Nombre del recurso.|  
|**% de contenciones**|Porcentaje de contenciones de este recurso con respecto a todos los eventos de contención de los datos de generación de perfiles.|  
  
## Subprocesos más contenidos  
 **Subprocesos más contenidos** enumera los subprocesos de la aplicación con el mayor número de eventos de contención.  Puede hacer clic en un nombre de subproceso para mostrar la vista Contenciones que proporciona una escala de tiempo detallada de las contenciones de recurso del subproceso.  
  
 **Subprocesos más contenidos** incluye los datos siguientes para cada subproceso.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**ID**|Identificador del subproceso.|  
|**Name**|Nombre del proceso al que pertenece el subproceso.|  
|**% de contenciones**|Porcentaje de contenciones de este recurso con respecto a todos los eventos de contención de los datos de generación de perfiles.|