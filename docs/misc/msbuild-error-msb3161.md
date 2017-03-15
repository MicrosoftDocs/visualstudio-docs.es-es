---
title: "Error de MSBuild MSB3161 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.CircularDependency"
helpviewer_keywords: 
  - "MSB3161"
ms.assetid: 2871d071-7c3a-4103-8b14-6ee56564a7f7
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3161
**MSB3161: Se detectó una dependencia circular entre los siguientes paquetes compilados: '\<paquete\>'**  
  
 Esta advertencia se genera cuando hay una dependencia circular en el gráfico de las dependencias de paquete de arranque \(por ejemplo: A→B→C→A\).  En estos casos, el arranque no puede determinar qué paquete debe instalarse primero.  
  
### Para corregir este error  
  
-   Quite la dependencia circular. Para ello, cambie las dependencias descritas en los archivos del paquete de arranque o no instale uno de los paquetes interdependientes.  
  
## Vea también  
 [Referencia de esquemas de productos y paquetes](../deployment/product-and-package-schema-reference.md)   
 [\<PackageFiles\> \(Elemento\)](../deployment/packagefiles-element-bootstrapper.md)