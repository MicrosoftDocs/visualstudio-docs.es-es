---
title: "Error de MSBuild MSB3143 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.CopyPackageError"
helpviewer_keywords: 
  - "MSB3143"
ms.assetid: b4278c8c-31df-4b4f-9ef9-7b9327e8ee77
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3143
**MSB3143: Error al intentar copiar '\<archivo\>' para el elemento '\<paquete\>': '\<error\>'**  
  
 Este error produce cuando los paquetes de arranque se copian en el directorio de resultados de la compilación.  Las causas posibles de este error son:  
  
-   No tiene permiso para copiar en el directorio de resultados de la compilación.  
  
-   El disco está lleno.  
  
 Estas son la mismas posibles razones que provocan el error de file.copy o directory.createdirectory.  
  
## Vea también  
 [Referencia de esquemas de productos y paquetes](../deployment/product-and-package-schema-reference.md)   
 [\<PackageFiles\> \(Elemento\)](../deployment/packagefiles-element-bootstrapper.md)