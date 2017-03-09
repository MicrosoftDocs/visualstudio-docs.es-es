---
title: "Error de MSBuild MSB3184 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.InvalidInputManifest"
helpviewer_keywords: 
  - "MSB3184"
ms.assetid: 2be9f8e9-04ee-4299-b79f-965ee57a1a34
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3184
**MSB3184: El manifiesto de entrada no es válido.**  
  
 Este error se genera cuando el proceso de compilación intenta cargar un archivo y espera que contenga un manifiesto de aplicación o de implementación. Sin embargo, resulta que contiene, por ejemplo, otro manifiesto o datos dañados.  
  
### Para corregir este error  
  
-   Compruebe que los manifiestos en el proyecto son válidos y adecuados.  
  
## Vea también  
 [\<PackageFiles\> \(Elemento\)](../deployment/packagefiles-element-bootstrapper.md)