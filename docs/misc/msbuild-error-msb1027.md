---
title: "Error de MSBuild MSB1027 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.CannotAutoDisableAutoResponseFile"
helpviewer_keywords: 
  - "MSB1027"
ms.assetid: 2ef8d643-616c-4608-be76-5c2c8e18a9e7
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB1027
**El modificador \/noautoresponse no se puede especificar en el archivo de respuesta automática MSBuild.rsp ni en ningún otro archivo de respuesta al que haga referencia el archivo de repuesta automática.**  
  
 El modificador **\/noautoresponse** se encontró en el archivo MSBuild.rsp o en otro archivo de respuesta incluido en el archivo MSBuild.rsp.  No se puede utilizar el archivo de respuesta automática para desactivarlo.  
  
### Para corregir este error  
  
-   Especifique otro archivo de respuesta.  
  
-   Quite el modificador **\/noautoresponse** del archivo de respuesta MSBuild.rsp.  
  
## Vea también  
 [Referencia de la línea de comandos](../msbuild/msbuild-command-line-reference.md)