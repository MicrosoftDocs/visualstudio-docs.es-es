---
title: "Error de MSBuild MSB1016 | Microsoft Docs"
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
  - "MSBuild.MissingVerbosityError"
helpviewer_keywords: 
  - "MSB1016"
ms.assetid: 967a9757-0513-48ae-bf1d-b1b019993c70
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB1016
**Especifique el nivel de contenido.**  
  
 Se debe especificar un nivel de contenido para el modificador **\/verbosity**.  
  
### Para corregir este error  
  
1.  Especifique el nivel de contenido con el formato `/verbosity:<level>`.  Los niveles de contenido disponibles son: q\[uiet\], m\[inimal\], n\[ormal\], d\[etailed\] y diag\[nostic\], por ejemplo, `/verbosity:quiet`,  `/verbosity:q` o  `/v:q`.  
  
## Vea también  
 [Referencia de la línea de comandos](../msbuild/msbuild-command-line-reference.md)