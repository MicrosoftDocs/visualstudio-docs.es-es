---
title: "Error de MSBuild MSB3023 | Microsoft Docs"
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
  - "MSBuild.Copy.NeedsDestination"
helpviewer_keywords: 
  - "MSB3023"
ms.assetid: 3505ad1e-d54f-4cb4-a299-ac03684cb391
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3023
**No se estableció el destino de la copia.  Especifique "'\<atributo\>'" o "'\<atributo\>'".**  
  
 Se debe especificar un destino para la tarea `Copy` usando uno de los atributos de tarea `DestinationFiles`y`DestinationDirectory`.  
  
### Para corregir este error  
  
-   Especifique `DestinationFiles`o`DestinationDirectory`para la tarea `Copy`.  
  
## Vea también  
 [Copy \(Tarea\)](../msbuild/copy-task.md)   
 [Tareas](../msbuild/msbuild-tasks.md)