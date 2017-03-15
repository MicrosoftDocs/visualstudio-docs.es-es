---
title: "Error de MSBuild MSB3153 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.PackageValidation"
helpviewer_keywords: 
  - "MSB3153"
ms.assetid: 937bb1ff-79f7-45a5-a085-525f4b48ea4e
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3153
**MSB3153: La validación XML no pasa por el elemento '\<paquete\>' ubicado en '\<carpeta\>'.**  
  
 Se genera esta advertencia cuando el manifiesto \(en concreto, package.xml\) no pasa la validación XML.  Los problemas específicos se indican en un mensaje de error posterior \([Error de MSBuild MSB3159](../misc/msbuild-error-msb3159.md) o [Error de MSBuild MSB3160](../misc/msbuild-error-msb3160.md)\).  
  
### Para corregir este error  
  
-   Resuelva los problemas de validación del manifiesto que se indican en los mensajes de error subsiguientes.  
  
## Vea también  
 [Referencia de esquemas de productos y paquetes](../deployment/product-and-package-schema-reference.md)   
 [\<PackageFiles\> \(Elemento\)](../deployment/packagefiles-element-bootstrapper.md)