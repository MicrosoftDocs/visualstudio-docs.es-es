---
title: "Error de MSBuild MSB3156 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.ProductValidation"
helpviewer_keywords: 
  - "MSB3156"
ms.assetid: 98b1bd42-9efe-44a2-8a43-476edc03590d
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3156
**MSB3156: La validación XML no pasa por el elemento '\<paquete\>' ubicado en '\<carpeta\>'.**  
  
 Se genera esta advertencia cuando el manifiesto \(en concreto, product.xml\) no pasa la validación XML.  Los problemas específicos se indican en un mensaje de error posterior \([Error de MSBuild MSB3159](../misc/msbuild-error-msb3159.md) o [Error de MSBuild MSB3160](../misc/msbuild-error-msb3160.md)\).  
  
### Para corregir este error  
  
-   Resuelva los problemas de validación del manifiesto que se indican en los mensajes de error subsiguientes.  
  
## Vea también  
 [Referencia de esquemas de productos y paquetes](../deployment/product-and-package-schema-reference.md)   
 [\<PackageFiles\> \(Elemento\)](../deployment/packagefiles-element-bootstrapper.md)