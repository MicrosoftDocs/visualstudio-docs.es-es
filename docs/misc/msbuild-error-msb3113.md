---
title: "Error de MSBuild MSB3113 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateManifest.ResolveFailedInReadWriteMode"
helpviewer_keywords: 
  - "MSB3113"
ms.assetid: 81e73738-e6ee-4651-9f48-acb1feef3ff5
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3113
**MSB3113: No se pudo encontrar el archivo '\<archivo\>'.**  
  
 Se genera este error cuando se encuentra una referencia irresoluble al crear un nuevo manifiesto.  Puede tener su origen en el archivo de proyecto o un parámetro de tarea.  
  
### Para corregir este error  
  
-   Compruebe en el archivo de proyecto \(y los parámetros de compilación si se trata de una compilación personalizada\) si hay conflictos entre las referencias de archivo.  
  
## Vea también  
 [\<PackageFiles\> \(Elemento\)](../deployment/packagefiles-element-bootstrapper.md)