---
title: "Error de MSBuild MSB3163 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.InvalidComponentsLocation"
helpviewer_keywords: 
  - "MSB3163"
ms.assetid: 35c5efbf-2fd7-478c-bb8e-3c4eabb3e4d4
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3163
**MSB3163: El parámetro de entrada de compilación 'ComponentsLocation\={ComponentsLocation}' compilado no es válido.  El valor debe ser 'HomeSite', 'Relative' o 'Absolute'.  Se volverá al valor predeterminado 'HomeSite'.**  
  
 Este error se genera cuando el valor especificado de la propiedad `ComponentsLocation` \(la ubicación desde la que se instalan los requisitos previos\) no es válido.  `ComponentsLocation` debe tener uno de estos tres valores: `HomeSite`, `Relative` o `Absolute`.  
  
## Vea también  
 [\<PackageFiles\> \(Elemento\)](../deployment/packagefiles-element-bootstrapper.md)