---
title: "Error de MSBuild MSB1024 | Microsoft Docs"
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
  - "MSBuild.MultipleSchemasError"
helpviewer_keywords: 
  - "MSB1024"
ms.assetid: dff30870-da1a-479f-998b-03d0f5e16088
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB1024
**Sólo se puede especificar un esquema para la validación del proyecto.**  
  
 Sólo se puede especificar un esquema para el modificador **\/validate**.  
  
### Para corregir este error  
  
1.  Especifique sólo un esquema para validar el proyecto usando el formato `/validate:<schema>`, por ejemplo, `/validate:MyExtendedBuildSchema.xsd`.  
  
## Vea también  
 [Referencia de la línea de comandos](../msbuild/msbuild-command-line-reference.md)