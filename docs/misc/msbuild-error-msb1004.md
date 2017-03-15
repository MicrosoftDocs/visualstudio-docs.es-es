---
title: "Error de MSBuild MSB1004 | Microsoft Docs"
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
  - "MSBuild.MissingTargetError"
helpviewer_keywords: 
  - "MSB1004"
ms.assetid: aed36761-ab07-486c-b5eb-48ccb1c387dd
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB1004
**Especifique el nombre del destino.**  
  
 Se debe especificar al menos un destino con el modificador **\/target**.  
  
### Para corregir este error  
  
1.  Especifique uno o varios destinos.  Puede utilizar una coma o un punto y coma para separar una lista de destinos, por ejemplo, `/target:Clean;Compile`.  Otra posibilidad consiste en repetir el modificador, por ejemplo, `/t:Clean /t:` `Compile`.  
  
## Vea también  
 [Destinos](../msbuild/msbuild-targets.md)   
 [Referencia de la línea de comandos](../msbuild/msbuild-command-line-reference.md)