---
title: "FormatUrl (Tarea) | Microsoft Docs"
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
  - "FormatUrl (tarea) [MSBuild]"
  - "MSBuild, FormatUrl (tarea)"
ms.assetid: 81114b67-520f-43b5-8891-224f68a78516
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# FormatUrl (Tarea)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Convierte una dirección URL en un formato de dirección URL correcto.  
  
## Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea `FormatUrl`.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`InputUrl`|Parámetro `String` opcional.<br /><br /> Especifica la dirección URL a la que se desea aplicar formato.|  
|`OutputUrl`|Parámetro de salida `String` opcional.<br /><br /> Especifica la dirección URL con formato.|  
  
## Comentarios  
 Además de tener los parámetros que se enumeran en la tabla, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que hereda de la clase <xref:Microsoft.Build.Utilities.Task>.  Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension \(Clase base\)](../msbuild/taskextension-base-class.md).  
  
## Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)