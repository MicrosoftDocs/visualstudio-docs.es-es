---
title: "VCMessage (Tarea) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.task.vcmessage"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "MSBuild (Visual C++), VCMessage (tarea)"
  - "VCMessage (tarea) (MSBuild (Visual C++))"
ms.assetid: 956675fd-05dc-40b4-856f-616145103498
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# VCMessage (Tarea)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Registra una advertencia y mensajes de error durante una compilación.  
  
## Comentarios  
 Esta tarea ayuda a implementar MSBuild para Visual C\+\+ y no está pensada para que la llame el usuario.  Para obtener más información, vea <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.  
  
## Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea **VCMessage** .  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|**Arguments**|Parámetro **String** opcional.<br /><br /> Una lista de mensajes delimitada por puntos y coma que se desea mostrar.|  
|**Code**|Parámetro **String** requerido.<br /><br /> Un número de error que califica el mensaje.|  
|**Type**|Parámetro **String** opcional.<br /><br /> Especifica el tipo del mensaje que se desea emitir.  Especifique `"Advertencia"` para emitir un mensaje de advertencia, o `"Error"` para emitir un mensaje de error.|  
  
## Vea también  
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)