---
title: "No se pudo obtener un flujo para el registro | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrApplicationLog_ExhaustedPossibleStreamNames"
ms.assetid: 33994f52-8efb-4790-a459-033e5c1db632
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se pudo obtener un flujo para el registro
No se pudo obtener un flujo para el registro. Los nombres de archivo potenciales basados en \<name\> ya están en uso.  
  
 La clase <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> no pudo crear un nuevo archivo de registro porque todos los posibles nombres de archivos de registro basados en \<name\> ya están en uso.  
  
 Si dispone de demasiados archivos de registro, podría ser un indicador de un problema de arquitectura con la aplicación. Consulte la documentación sobre la clase <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> para más información.  
  
### Para corregir este error  
  
1.  Establezca la propiedad <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> en <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption> o <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption> para incluir una marca de fecha en el nombre del archivo de registro.  
  
2.  Almacene los registros existentes y quítelos del equipo para permitir que el objeto <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> cree nuevos registros.  
  
## Vea también  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>   
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A>   
 [My.Application.Log \(Objeto\)](/dotnet/visual-basic/language-reference/objects/my-application-log-object)   
 [My.Log \(Objeto\)](/dotnet/visual-basic/language-reference/objects/my-log-object)