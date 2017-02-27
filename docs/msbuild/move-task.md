---
title: "Move (Tarea) | Microsoft Docs"
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
helpviewer_keywords: 
  - "Move (tarea) [MSBuild]"
  - "MSBuild, Move (tarea)"
ms.assetid: d1405347-1309-4f18-b565-905408093d59
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# Move (Tarea)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mueve archivos a una nueva ubicación.  
  
## Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea `Move`.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`DestinationFiles`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica la lista de archivos en la que se moverán los archivos de código fuente.  Se espera que esta lista sea una asignación unívoca a la lista especificada en el parámetro `SourceFiles`.  Es decir, el primer archivo especificado en `SourceFiles` se moverá a la primera ubicación especificada en `DestinationFiles` y así en adelante.|  
|`DestinationFolder`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica el directorio al que desea mover los archivos.|  
|`MovedFiles`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contiene los elementos que se movieron correctamente.|  
|`OverwriteReadOnlyFiles`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, sobrescribe los archivos aunque estén marcados como archivos de solo lectura.|  
|`SourceFiles`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` requerido.<br /><br /> Especifica los archivos que se van a mover.|  
  
## Comentarios  
 Se debe especificar el parámetro `DestinationFolder` o el parámetro `DestinationFiles`, pero no ambos.  Si se especifican los dos, en la tarea se produce un error y se registra un error.  
  
 Además de tener los parámetros que se enumeran en la tabla, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que hereda de la clase <xref:Microsoft.Build.Utilities.Task>.  Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension \(Clase base\)](../msbuild/taskextension-base-class.md).  
  
## Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)