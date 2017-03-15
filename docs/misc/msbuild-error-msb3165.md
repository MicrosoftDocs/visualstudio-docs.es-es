---
title: "Error de MSBuild MSB3165 | Microsoft Docs"
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
  - "vsdeploy.chm:13165"
  - "MSBuild.GenerateBootstrapper.DifferingPublicKeys"
helpviewer_keywords: 
  - "MSB3165"
ms.assetid: 2f50462e-947d-4211-b197-e58eddcfd373
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3165
**MSB3165: El valor del atributo '\<clave pública\>' en '\<paquete\>' no coincide con el del archivo '\<archivo\>'.**  
  
 Esta advertencia se produce cuando la clave pública especificada en el archivo de paquete de arranque no coincide con la firma del paquete redistribuible en el disco o cuando el paquete redistribuible no está firmado.  La compilación tomará el valor de clave pública del paquete redistribuible en el disco si está firmado, o bien, tomará el código hash del paquete redistribuible en el disco si no está firmado.  
  
## Vea también  
 [\<PackageFiles\> \(Elemento\)](../deployment/packagefiles-element-bootstrapper.md)   
 [Referencia de esquemas de productos y paquetes](../deployment/product-and-package-schema-reference.md)