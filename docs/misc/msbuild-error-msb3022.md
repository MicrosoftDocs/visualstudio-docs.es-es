---
title: "Error de MSBuild MSB3022 | Microsoft Docs"
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
  - "MSBuild.Copy.ExactlyOneTypeOfDestination"
helpviewer_keywords: 
  - "MSB3022"
ms.assetid: 74ebcced-8a56-4502-8fef-43d36c79a640
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3022
**"'\<atributo\>'" y "'\<atributo\>'" se especificaron como parámetros de entrada en el archivo de proyecto.  Elija uno de los dos.**  
  
 Para la tarea `Copy`, debe especificar `DestinationFiles` o `DestinationDirectory`, pero no ambos.  
  
### Para corregir este error  
  
-   En el archivo de proyecto, especifique `DestinationFiles` o `DestinationDirectory` para la tarea `Copy`.  
  
## Vea también  
 [Copy \(Tarea\)](../msbuild/copy-task.md)   
 [Tareas](../msbuild/msbuild-tasks.md)