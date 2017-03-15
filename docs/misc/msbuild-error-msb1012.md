---
title: "Error de MSBuild MSB1012 | Microsoft Docs"
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
  - "MSBuild.MissingResponseFileError"
helpviewer_keywords: 
  - "MSB1012"
ms.assetid: 6e09e21d-9f64-4a8c-adec-f8efb28b7ac2
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB1012
**Especifique un archivo de respuesta.**  
  
 Se debe especificar un archivo de respuesta para el modificador @.  
  
### Para corregir este error  
  
-   Especifique un archivo de respuesta.  La sintaxis es @\<nombre de archivo\>, por ejemplo, `@BuildHW.txt`  
  
-   No incluya el modificador @ en la línea de comandos.  
  
## Vea también  
 [Referencia de la línea de comandos](../msbuild/msbuild-command-line-reference.md)