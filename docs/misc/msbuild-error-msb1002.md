---
title: "Error de MSBuild MSB1002 | Microsoft Docs"
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
  - "MSBuild.UnexpectedParametersError"
helpviewer_keywords: 
  - "MSB1002"
ms.assetid: 798c9690-6d99-4f21-a491-ab44d3f3c552
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB1002
**Este modificador no toma ningún parámetro.**  
  
 No se pueden definir parámetros para este modificador.  Sólo se requiere el nombre del modificador y no debe ir seguido de dos puntos.  
  
### Para corregir este error  
  
-   Escriba el comando sin parámetros para este modificador, es decir, en lugar de escribir `msbuild /<switch>:<parameters>`, escriba `msbuild /<switch>`.  
  
-   Quite los dos puntos que siguen al nombre del modificador, es decir, en lugar de escribir `msbuild /<switch>:`, escriba `msbuild /<switch>`.  
  
## Vea también  
 [Referencia de la línea de comandos](../msbuild/msbuild-command-line-reference.md)