---
title: "Error de MSBuild MSB3128 | Microsoft Docs"
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
  - "GenerateManifest.ManifestsSignedHashExcluded"
helpviewer_keywords: 
  - "MSB3128"
ms.assetid: e8612a4b-4016-48d2-b5f0-a1091bfe8cb1
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3128
**MSB3128: Los manifiestos de ClickOnce no se pueden firmar porque contienen una o varias referencias a las que no se ha aplicado un algoritmo hash.**  
  
 Cuando se publica una aplicación que tiene una manifiesto firmado, todos los archivos deben estar incluidos en el hash.  
  
### Para corregir este error  
  
1.  Vaya a la página **Publicar** del **Diseñador de proyectos**.  
  
2.  Haga clic en **Archivos de aplicación**.  
  
3.  Establezca el valor **Hash** en **Incluir** en todos los archivos que se van a publicar.  
  
## Vea también  
 [Panel Publicar, Diseñador de proyectos](../ide/reference/publish-page-project-designer.md)