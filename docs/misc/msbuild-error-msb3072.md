---
title: "Error de MSBuild MSB3072 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.Exec.MissingCommandError"
helpviewer_keywords: 
  - "MSB3072"
ms.assetid: c8468e1c-d8c7-441c-b274-123ac856f147
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3072
**La tarea "Exec" necesita un comando para ejecutarse.**  
  
 El atributo `Command` es un atributo necesario para la tarea `Exec`.  
  
### Para corregir este error  
  
1.  En el archivo de proyecto, especifique el atributo `Command` para la tarea `Exec`.  
  
## Vea también  
 [Exec \(Tarea\)](../msbuild/exec-task.md)   
 [Tareas](../msbuild/msbuild-tasks.md)