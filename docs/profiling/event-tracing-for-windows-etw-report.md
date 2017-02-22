---
title: "Informe Seguimiento de eventos para Windows (ETW) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "informe ETW de generación de perfiles"
  - "informe de Seguimiento de eventos para Windows de generación de perfiles"
ms.assetid: 81e88162-b88a-40b6-8b85-a232c8096a47
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Informe Seguimiento de eventos para Windows (ETW)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El informe de seguimiento de eventos para Windows \(ETW\) muestra los eventos ETW grabados en una sesión de rendimiento de las Herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Los datos ETW se recopilan en un archivo binario \(.etl\).  
  
> [!NOTE]
>  No puede mostrar los informes ETW en la interfaz de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Para obtener información sobre cómo recopilar datos ETW mediante las herramientas de generación de perfiles de la interfaz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vea [Cómo: Recopilar datos de Seguimiento de eventos para Windows \(ETW\)](../Topic/How%20to:%20Collect%20Event%20Tracing%20for%20Windows%20\(ETW\)%20Data.md).  
  
-   Para obtener información sobre cómo recopilar datos ETW utilizando las herramientas de línea de comandos de [VSPerfCmd](../profiling/vsperfcmd.md), vea [Eventos](../profiling/events-vsperfcmd.md).  
  
-   Genere el informe ETW utilizando el comando **VSReport\/Summary:ETW**.  Para obtener más información, vea [VSPerfReport](../profiling/vsperfreport.md).  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Marca de tiempo**|Identifica el momento en que se produjo el evento.|  
|**Id. de proceso**|Identifica el proceso que generó el evento.|  
|**Id. de subproceso**|Identifica el subproceso que generó el evento.|  
|**Descripción**|Identifica el proveedor de eventos.|  
|**Tipo**|Identifica el tipo de evento.|  
|**Propiedades**|Propiedades del evento.  Cada evento es un par de nombre y valor delimitado por comas y encerrado entre corchetes.|