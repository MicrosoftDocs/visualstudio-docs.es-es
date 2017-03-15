---
title: "Error de MSBuild MSB3157 | Microsoft Docs"
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
  - "vsdeploy.chm:13157"
  - "MSBuild.GenerateBootstrapper.UsingProductCulture"
helpviewer_keywords: 
  - "MSB3157"
ms.assetid: ccfcbea4-eb9b-42ae-9908-47079ecc84a7
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3157
**MSB3157: No se pudo encontrar la correspondencia para la referencia cultural '\<referencia cultural\>' para el elemento '\<paquete\>'.  Se utilizará la referencia cultural '\<referencia cultural\>'.**  
  
 Esta advertencia se genera cuando el producto especificado no encuentra un archivo de manifiesto del paquete \(package.xml\) que utilice la referencia cultural especificada.  
  
### Para corregir este error  
  
-   Proporcione el archivo de manifiesto del paquete apropiado.  
  
## Vea también  
 [\<PackageFiles\> \(Elemento\)](../deployment/packagefiles-element-bootstrapper.md)