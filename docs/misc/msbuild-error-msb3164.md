---
title: "Error de MSBuild MSB3164 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.PackageHomeSiteMissing"
helpviewer_keywords: 
  - "MSB3164"
ms.assetid: 5a1e31fc-0322-4d4e-8c26-013b1efb82c9
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3164
**MSB3164: No se proporcionó ningún atributo 'HomeSite' para '\<paquete\>'. El paquete se publicará en la misma ubicación que el arranque.**  
  
 Esta advertencia se genera cuando el usuario desea utilizar HomeSite, pero no está disponible la información apropiada de HomeSite para el paquete especificado.  
  
### Para corregir este error  
  
-   Actualice los archivos de manifiesto para incluir la información de HomeSite.  
  
-   Otra solución es no utilizar HomeSite.  
  
## Vea también  
 [\<PackageFiles\> \(Elemento\)](../deployment/packagefiles-element-bootstrapper.md)