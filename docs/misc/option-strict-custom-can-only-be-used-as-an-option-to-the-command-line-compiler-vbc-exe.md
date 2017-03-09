---
title: "Option Strict Custom solo se puede usar como una opci&#243;n del compilador de la l&#237;nea de comandos (vbc.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31141"
  - "bc31141"
helpviewer_keywords: 
  - "BC31141"
ms.assetid: c32ae8ff-aacc-40b4-960a-6f2d5d246671
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict Custom solo se puede usar como una opci&#243;n del compilador de la l&#237;nea de comandos (vbc.exe)
La instrucción `Option Strict` solo toma `On` y `Off` como argumentos; `Option Strict Custom` no está permitido.  
  
 Use la opción del compilador `/optionstrict:custom` para advertir cuando no se respete la semántica estricta del lenguaje.  
  
 **Identificador de error:** BC31141  
  
### Para corregir este error  
  
1.  Quite `Option Strict Custom` del código fuente.  
  
2.  Especifique la opción `/optionstrict:custom`. Para obtener más información, consulta [\/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict).  
  
## Vea también  
 [Option \<palabra clave\> \(Instrucción\)](../Topic/Option%20%3Ckeyword%3E%20Statement.md)   
 [Option Strict \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [\/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict)