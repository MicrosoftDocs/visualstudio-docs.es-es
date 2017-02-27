---
title: "ConvertToAbsolutePath (Tarea) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#ConvertToAbsolutePath"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "ConvertToAbsolutePath (tarea) [MSBuild]"
  - "MSBuild, ConvertToAbsolutePath (tarea)"
ms.assetid: f1af2cb8-b4ef-4a72-be80-22fa526c4491
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# ConvertToAbsolutePath (Tarea)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Convierte una ruta de acceso relativa, o una referencia, en una ruta de acceso absoluta.  
  
## Parámetros de la tarea  
 En la siguiente tabla se describen los parámetros de la tarea `ConvertToAbsolutePath`.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Paths`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` requerido.<br /><br /> Lista de las rutas de acceso relativas que se van a convertir en rutas de acceso absolutas.|  
|`AbsolutePaths`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Lista de las rutas de acceso absolutas de los elementos que se han pasado.|  
  
## Comentarios  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que hereda de la clase <xref:Microsoft.Build.Utilities.Task>.  Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension \(Clase base\)](../msbuild/taskextension-base-class.md).  
  
## Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)