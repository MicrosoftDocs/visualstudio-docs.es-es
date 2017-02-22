---
title: "ResolveNonMSBuildProjectOutput (Tarea) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
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
  - "MSBuild, ResolveNonMSBuildProjectOutput (tarea)"
  - "ResolveNonMSBuildProjectOutput (tarea) [MSBuild]"
ms.assetid: a0b8fcec-8c8d-4867-85ac-5304c5108e5e
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# ResolveNonMSBuildProjectOutput (Tarea)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Determina los archivos de salida de las referencias de proyecto que no son de MSBuild.  
  
## Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea `ResolveNonMSBuildProjectOutput`.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`PreresolvedProjectOutputs`|Parámetro `String` opcional.<br /><br /> Especifica una cadena XML que contiene los resultados de proyecto resueltos.|  
|`ProjectReferences`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]`  requerido.<br /><br /> Especifica las referencias del proyecto.|  
|`ResolvedOutputPaths`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contiene la lista de trayectorias de referencia resueltas \(y conserva los atributos de referencia del proyecto original\).|  
|`UnresolvedProjectReferences`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contiene la lista de elementos de referencia de proyecto que no se pudieron resolver mediante la lista de resultados resuelta previamente.<br /><br /> Porque Visual Studio solo resuelve previamente proyectos que no son de MSBuild, esto significa que las referencias del proyecto de esta lista están en el formato de MSBuild.|  
  
## Comentarios  
 Además de tener los parámetros que se enumeran en la tabla, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que hereda de la clase <xref:Microsoft.Build.Utilities.Task>.  Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension \(Clase base\)](../msbuild/taskextension-base-class.md).  
  
## Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)