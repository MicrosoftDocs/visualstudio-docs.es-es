---
title: "Error de MSBuild MSB1007 | Microsoft Docs"
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
  - "MSBuild.MissingLoggerError"
helpviewer_keywords: 
  - "MSB1007"
ms.assetid: bf45dbc3-50cd-488a-87df-9e647cd71f10
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB1007
**Especifique un registrador.**  
  
 Se debe especificar un registrador para el modificador **\/logger**.  
  
### Para corregir este error  
  
1.  Especifique un registrador utilizando tanto la clase como el ensamblado de registrador.  La sintaxis de `<logger>` es:  
  
     `<logger class>,<logger assembly>[;<logger parameters>]`  
  
     La sintaxis de `<logger class>` es:  
  
    ```  
    [<partial or full namespace>.]<logger class name>  
    ```  
  
     La sintaxis de `<logger assembly>` es:  
  
    ```  
    {<assembly name>[,<strong name>] | <assembly file>}  
    ```  
  
     Los `<logger parameters>` son opcionales y se pasan al registrador tal como se hayan escrito.  
  
     Ejemplos del modificador **\/logger** son:  
  
     `/logger:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`  
  
     `/logger:XMLLogger,C:\Loggers\MyLogger.dll`  
  
     `/logger:XMLLogger,..  \Loggers\MyLogger.dll;OutputAsHTML`  
  
## Vea también  
 [Referencia de la línea de comandos](../msbuild/msbuild-command-line-reference.md)