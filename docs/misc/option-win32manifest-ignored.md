---
title: "Se ignor&#243; la opci&#243;n /win32manifest | Microsoft Docs"
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
  - "vbc2034"
  - "bc2034"
helpviewer_keywords: 
  - "BC2034"
ms.assetid: 8009553a-f6ba-4d2b-8ddd-8a9357bc928e
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Se ignor&#243; la opci&#243;n /win32manifest
Se ignoró la opción \/win32manifest. Solo se puede especificar cuando el destino es un ensamblado.  
  
 El compilador de Visual Basic se pasa a la opción `/win32manifest` del compilador cuando la opción `/target` está establecida en `module`.  
  
 **Identificador de error:** BC2034  
  
### Para corregir este error  
  
1.  Quite la opción `/win32manifest` del compilador o establezca la opción `/target` en `exe`, `winexe` o `library`.  
  
## Vea también  
 [\/target](/dotnet/visual-basic/reference/command-line-compiler/target)   
 [\/win32manifest](/dotnet/visual-basic/reference/command-line-compiler/win32manifest)   
 [Compilador de línea de comandos de Visual Basic](/dotnet/visual-basic/reference/command-line-compiler/index)