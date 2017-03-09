---
title: "Error de MSBuild MSB3182 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.TargetPathTooLong"
helpviewer_keywords: 
  - "MSB3182"
ms.assetid: b257a206-b12b-453b-97d8-2cb9a0d3dcc9
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3182
**MSB3182: El nombre de archivo '\<archivo\>' supera los '\<longitud\>' caracteres.**  
  
 Se genera esta advertencia cuando el valor de la propiedad `TargetPath` es demasiado largo.  Puede aplicarse tanto al manifiesto de aplicación como al manifiesto de implementación.  
  
### Para corregir este error  
  
-   Edite el valor de la propiedad `TargetPath` para aplicar un valor más corto.  
  
## Vea también  
 [\<PackageFiles\> \(Elemento\)](../deployment/packagefiles-element-bootstrapper.md)