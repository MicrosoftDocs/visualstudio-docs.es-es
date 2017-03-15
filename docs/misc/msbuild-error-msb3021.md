---
title: "Error de MSBuild MSB3021 | Microsoft Docs"
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
  - "MSBuild.Copy.Error"
helpviewer_keywords: 
  - "MSB3021"
ms.assetid: 8cb3a860-6916-4406-b5c7-b1106b44b92a
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3021
**No se puede copiar "'\<archivo\>'" en "'\<archivo\>'". '  \<error\>'**  
  
 La tarea `Copy` no puede copiar el archivo especificado.  
  
### Para corregir este error  
  
-   Compruebe si otra aplicación bloquea el archivo de destino \(en uso\).  Asegúrese de que tiene permiso para leer el archivo de origen y escribir el archivo de destino en la carpeta de destino.  Si la ruta de destino es muy larga, puede ser necesario copiarlo en una ubicación diferente.  
  
## Vea también  
 [Copy \(Tarea\)](../msbuild/copy-task.md)   
 [Tareas](../msbuild/msbuild-tasks.md)