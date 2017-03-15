---
title: "El tipo implementado debe ser una interfaz | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30232"
  - "vbc30232"
helpviewer_keywords: 
  - "BC30232"
ms.assetid: 63f3dd4c-2f99-4070-b506-2fa808df24d4
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El tipo implementado debe ser una interfaz
Una instrucción `Implements` no especifica una interfaz. Una clase solo puede implementar una interfaz.  
  
 **Id. de error:** BC30232  
  
### Para corregir este error  
  
1.  Asegúrese de que el nombre de la interfaz está escrito correctamente.  
  
2.  Si la instrucción especifica una clase, considere la posibilidad de usar la instrucción `Inherits`.  
  
## Vea también  
 [Implements \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/implements-statement)   
 [Inherits \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/inherits-statement)   
 [NO ESTÁ EN LA COMPILACIÓN: Herencia en Visual Basic](http://msdn.microsoft.com/es-es/e5e6e240-ed31-4657-820c-079b7c79313c)