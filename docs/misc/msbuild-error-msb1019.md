---
title: "Error de MSBuild MSB1019 | Microsoft Docs"
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
  - "MSBuild.InvalidLoggerError"
helpviewer_keywords: 
  - "MSB1019"
ms.assetid: 5d0169f7-f878-433a-ac30-d9d6010130af
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB1019
**El modificador del registrador no está formado correctamente.**  
  
 No se ha especificado correctamente el modificador **\/logger**.  Para especificar un registrador, es preciso proporcionar al menos el ensamblado de registrador, o bien, si desea especificar explícitamente el registrador que desee cargar, proporcione la clase de registrador y el ensamblado de registrador.  Los parámetros del registrador son opcionales.  
  
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
  
     Ejemplo: \/`logger:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`  
  
## Vea también  
 [Referencia de la línea de comandos](../msbuild/msbuild-command-line-reference.md)   
 [Registradores de compilación](../msbuild/build-loggers.md)