---
title: "FindAppConfigFile (Tarea) | Microsoft Docs"
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
  - "FindAppConfigFile (tarea) [MSBuild]"
  - "MSBuild, FindAppConfigFile (tarea)"
ms.assetid: e292de3e-7482-4426-83ce-d921061808bf
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# FindAppConfigFile (Tarea)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Busca el archivo app.config, si hay alguno, en las listas proporcionadas.  
  
## Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea `FindAppConfigFile`.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`AppConfigFile`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica el primer elemento coincidente encontrado en la lista, si hay alguno.|  
|`PrimaryList`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` requerido.<br /><br /> Especifica la lista principal en la que se va a buscar.|  
|`SecondaryList`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` requerido.<br /><br /> Especifica la lista secundaria en la que se va a buscar.|  
|`TargetPath`|Parámetro `String` requerido.<br /><br /> Especifica el valor que se desea agregar como metadatos.|  
  
## Comentarios  
 Además de tener los parámetros que se enumeran en la tabla, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que hereda de la clase <xref:Microsoft.Build.Utilities.Task>.  Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension \(Clase base\)](../msbuild/taskextension-base-class.md).  
  
## Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)