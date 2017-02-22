---
title: "FormatVersion (Tarea) | Microsoft Docs"
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
ms.assetid: 96e692f6-b581-46ca-8cc9-441a1861e371
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# FormatVersion (Tarea)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Anexa el número de revisión al número de versión.  
  
-   Caso nº 1: Entrada: versión\=\<no definida\>; Revisión\=\<no importa\>; Salida: OutputVersion\="1.0.0.0"  
  
-   Caso nº 2: Entrada: Versión\="1.0.0.\*" Revisión\="5" Salida: OutputVersion\="1.0.0.5"  
  
-   Caso nº 3: Entrada: Versión\="1.0.0.0" Revisión\=\<no importa\>; Salida: OutputVersion\="1.0.0.0"  
  
## Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea `FormatVersion`.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`FormatType`|Parámetro `String` opcional.<br /><br /> Especifica el tipo de formato.<br /><br /> -   "Version" \= versión.<br />-   "Path"\= reemplazar "." por "\_";|  
|`OutputVersion`|Parámetro de salida `String` opcional.<br /><br /> Especifica la versión de salida que incluye el número de revisión.|  
|`Revision`|Parámetro `Int32` opcional.<br /><br /> Especifica la revisión que se desea anexar a la versión.|  
|`Version`|Parámetro `String` opcional.<br /><br /> Especifica la cadena de número de versión al que se desea aplicar formato.|  
  
## Comentarios  
 Además de tener los parámetros que se enumeran en la tabla, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que hereda de la clase <xref:Microsoft.Build.Utilities.Task>.  Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension \(Clase base\)](../msbuild/taskextension-base-class.md).  
  
## Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)