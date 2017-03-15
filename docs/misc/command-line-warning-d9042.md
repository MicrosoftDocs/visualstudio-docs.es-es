---
title: "Advertencia de la l&#237;nea de comandos D9042 | Microsoft Docs"
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
  - "D9042"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "D9042"
ms.assetid: d710693b-e422-40b2-b2dd-79e1b163b9e6
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Advertencia de la l&#237;nea de comandos D9042
valor 'valor' no válido para 'opción'; se supone 'valor'; las advertencias de análisis de código no están disponibles en esta edición del compilador  
  
 Se agregó una advertencia de análisis de código a la opción de línea de comandos **\/wd**, **\/we**, **\/wo** o **\/wl** y se especificó la opción de línea de comandos **\/analyze** en una plataforma que no admite el análisis de código.  La solución es pasarse a la versión x86 de Visual Studio Team System o quitar la opción de línea de comandos **\/analyze**.  
  
## Ejemplo  
 El ejemplo de línea de comandos siguiente genera la advertencia D9042 en un sistema x64 o Itanium:  
  
```  
cl /EHsc /LD /wd6001 /analyze filename.cpp  
```  
  
 La solución es pasarse a la versión x86 de Visual Studio Team System o quitar las opciones de línea de comandos **\/analyze** y **\/wd6001**.  
  
## Vea también  
 [Errores de la línea de comandos de D8000 a D9000](/visual-cpp/error-messages/tool-errors/command-line-errors-d8000-through-d9999)   
 [Opciones del compilador](/visual-cpp/build/reference/compiler-options)