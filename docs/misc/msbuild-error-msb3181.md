---
title: "Error de MSBuild MSB3181 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.DuplicateTargetPath"
helpviewer_keywords: 
  - "MSB3181"
ms.assetid: 49349fc2-3fa1-470d-a5cb-6ad72b93f408
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3181
**MSB3181: Dos o más archivos tienen la misma ruta de acceso '\<ruta de acceso\>'.**  
  
 Esta advertencia se genera durante la generación del manifiesto de aplicación cuando dos o más de los archivos o ensamblados a los que se hace referencia comparten la misma ruta de acceso de destino.  La ruta de acceso incluye el nombre de archivo y todos estos ensamblados se sobrescribirán entre sí en tiempo de implementación.  
  
## Vea también  
 [\<PackageFiles\> \(Elemento\)](../deployment/packagefiles-element-bootstrapper.md)