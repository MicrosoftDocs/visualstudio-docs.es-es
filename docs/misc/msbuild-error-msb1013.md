---
title: "Error de MSBuild MSB1013 | Microsoft Docs"
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
  - "MSBuild.RepeatedResponseFileError"
helpviewer_keywords: 
  - "MSB1013"
ms.assetid: 3e85c710-99e6-4141-b058-63a144a06454
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB1013
**El archivo de respuesta se especificó dos veces.  Un archivo de respuesta sólo se puede especificar una vez.**  
  
 La línea de comandos contiene referencias a varios archivos de respuesta.  Por ejemplo, `msbuild @response.rsp @response.rsp`.  
  
 Este error también puede producirse si el archivo de respuesta especificado incluye una referencia a otro archivo de respuesta que incluya una referencia al archivo de respuesta original.  Un archivo de respuesta sólo se puede especificar una vez en cada compilación.  
  
### Para corregir este error  
  
-   Quite la referencia duplicada al archivo de respuesta.  Por ejemplo, en lugar de utilizar `msbuild @response.rsp @response.rsp`, use `msbuild @response.rsp`.  
  
-   Quite la referencia al archivo de respuesta original del archivo de respuesta al que hace referencia.  
  
## Vea también  
 [Referencia de la línea de comandos](../msbuild/msbuild-command-line-reference.md)