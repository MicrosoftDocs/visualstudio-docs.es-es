---
title: "C&#243;mo: Filtrar informes desde la l&#237;nea de comandos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# C&#243;mo: Filtrar informes desde la l&#237;nea de comandos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si usa las opciones del comando **VSPerfReport** , puede filtrar los informes a un segmento específico de tiempo del archivo de datos de generación de perfiles o restringir los datos a uno o varios procesos o subprocesos.  Para obtener más información sobre este comando, vea [VSPerfReport](../profiling/vsperfreport.md).  
  
|Opciones|Descripción|  
|--------------|-----------------|  
|**StartTime:**\[*Value*\]|Sólo muestra los datos recopilados tras el valor \(en milisegundos\).|  
|**EndTime:**\[*Value*\]|Sólo muestra los datos recopilados antes del valor \(en milisegundos\).|  
|**FilterFile:** `VSPFFile`|Especifica la ubicación de un archivo de filtro que se generó en la ventana **Informe de rendimiento de Visual Studio**.|  
|**MsFilter:**\[*StartTime,Duration*\]|Solo se muestran los datos de `StartTime` hasta la longitud de `Duration` \(en milisegundos\).|  
|**Process:**\[*Pid*\]|Sólo muestra los datos del proceso especificado.|  
|**Thread:**\[*ThreadID*\]|Sólo muestra los datos del subproceso especificado.|  
|**Thread:**\[*ThreadID,ProcessID*\]|Solo se muestran los datos del subproceso especificado asociado al proceso especificado.|