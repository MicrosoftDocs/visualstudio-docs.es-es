---
title: "Error de MSBuild MSB3071 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.Exec.AllDriveLettersMappedError"
helpviewer_keywords: 
  - "MSB3071"
ms.assetid: 8afbc6ec-e399-4f06-a30b-f33c87642ef7
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3071
**Todas las letras de unidad de la A: a la Z: se están utilizando.  Puesto que el directorio de trabajo "'\<ruta de acceso\>'" es una ruta UNC, la tarea "Exec" necesita una letra de unidad disponible a la que asignar la ruta UNC.  Desconecte uno o más recursos compartidos para liberar letras de unidad o especifique un directorio de trabajo local antes de volver a intentar este comando.**  
  
 Todas las letras de unidad \(de la A: a la Z:\) están actualmente en uso.  Dado que el directorio de trabajo especificado es una ruta UNC, la tarea `Exec` necesita una letra de unidad disponible a la que asignar la ruta UNC.  
  
### Para corregir este error  
  
-   Desconecte uno o varios recursos compartidos para liberar letras de unidad.  
  
-   Especifique un directorio de trabajo local antes de volver a ejecutar este comando.  
  
## Vea también  
 [Exec \(Tarea\)](../msbuild/exec-task.md)