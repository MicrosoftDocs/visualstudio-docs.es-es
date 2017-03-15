---
title: "Error de MSBuild MSB3177 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.AllowPartiallyTrustedCallers"
helpviewer_keywords: 
  - "MSB3177"
ms.assetid: 0b2417d5-3bc3-4169-b69c-a4a3cbf47882
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3177
**MSB3177: La referencia '\<referencia\>' no permite llamadores de confianza parcial.**  
  
 Esta advertencia aparece durante la generación de un manifiesto de aplicación cuando la aplicación es de confianza parcial y se agregó *referencia* como una referencia de proyecto, tiene un nombre seguro y no tiene el atributo APTCA.  
  
### Para corregir este error  
  
-   Agregue el atributo APTCA al ensamblado al que se hace referencia, o bien, deje de utilizarlo si la primera solución no es posible.  
  
## Vea también  
 [\<PackageFiles\> \(Elemento\)](../deployment/packagefiles-element-bootstrapper.md)