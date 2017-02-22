---
title: "FindInList (Tarea) | Microsoft Docs"
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
  - "FindInList (tarea) [MSBuild]"
  - "MSBuild, FindInList (tarea)"
ms.assetid: d49b9f84-52a2-4242-9269-b741a7a7e9f7
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# FindInList (Tarea)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En una lista especificada, busca un elemento cuya especificación coincida.  
  
## Parámetros  
 En la siguiente tabla se describen los parámetros de [FindInList Task](../msbuild/findinlist-task.md).  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`CaseSensitive`|Parámetro `Boolean` opcional.<br /><br /> Si el valor es `true`, la búsqueda distingue entre mayúsculas y minúsculas; de lo contrario, no lo hace.  El valor predeterminado es `true`.|  
|`FindLastMatch`|Parámetro `Boolean` opcional.<br /><br /> Si el valor es `true`, devuelve la última coincidencia; de lo contrario, devuelve la primera coincidencia.  El valor predeterminado es `false`.|  
|`ItemFound`|Parámetro de salida de sólo lectura <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Primer elemento coincidente encontrado en la lista, si hay alguno.|  
|`ItemSpecToFind`|Parámetro `String` requerido.<br /><br /> Itemspec que se va a buscar.|  
|`List`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` requerido.<br /><br /> Lista en la que se va a buscar el itemspec.|  
|`MatchFileNameOnly`|Parámetro `Boolean` opcional.<br /><br /> Si el valor es `true`, coincide solamente con la parte del nombre de archivo del itemspec; de lo contrario, coincide con todo el itemspec.  El valor predeterminado es `true`.|  
  
## Comentarios  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que hereda de la clase <xref:Microsoft.Build.Utilities.Task>.  Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension \(Clase base\)](../msbuild/taskextension-base-class.md).  
  
## Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)