---
title: "Task Base (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 6c3f6238-b9f0-4325-b8b0-de61090bd0a2
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# Task Base (Clase)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Muchas de las tareas se heredan en última instancia de la clase <xref:Microsoft.Build.Utilities.Task>.  Esta clase agrega varios parámetros a las tareas que derivan de ellos.  Estos parámetros se enumeran en este documento.  
  
## Parámetros  
 La tabla siguiente describe los parámetros de esta clase base.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>|Parámetro <xref:Microsoft.Build.Framework.IBuildEngine> opcional.<br /><br /> Especifica la interfaz de motor de compilación disponible para las tareas.  El motor de compilación establece automáticamente este parámetro para que las tareas puedan volver a llamarla.|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>|Parámetro <xref:Microsoft.Build.Framework.IBuildEngine2> opcional.<br /><br /> Especifica la interfaz de motor de compilación disponible para las tareas.  El motor de compilación establece automáticamente este parámetro para que las tareas puedan volver a llamarla.<br /><br /> Se trata de una propiedad de conveniencia para que los autores de tareas que hereden de esta clase no tengan que convertir el valor de `IBuildEngine` en `IBuildEngine2`.|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A>|Parámetro <xref:Microsoft.Build.Framework.IBuildEngine3> opcional.<br /><br /> Especifica la interfaz de motor de compilación proporcionada por el host.|  
|<xref:Microsoft.Build.Utilities.Task.HostObject%2A>|Parámetro <xref:Microsoft.Build.Framework.ITaskHost> opcional.<br /><br /> Especifica la instancia del objeto host \(puede ser null\).  El motor de compilación establece esta propiedad si el entorno IDE del host tiene un objeto host asociado a esta tarea concreta.|  
|<xref:Microsoft.Build.Utilities.Task.Log%2A>|Parámetro de solo lectura <xref:Microsoft.Build.Utilities.TaskLoggingHelper> opcional.<br /><br /> El objeto auxiliar de registro.|  
  
## Vea también  
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)   
 [Tareas](../msbuild/msbuild-tasks.md)