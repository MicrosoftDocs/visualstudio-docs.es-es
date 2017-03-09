---
title: "Error del compilador CS1632 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1632"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1632"
ms.assetid: fa18061a-8c6c-4788-b74e-62bacb16aed8
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1632
El control no puede abandonar el cuerpo de un método anónimo o de una expresión lambda  
  
 Este error se produce si una instrucción de salto \(**break**, `goto`, **continue**, etc.\) intenta mover el control fuera de un bloque de método anónimo. Un bloque de método anónimo es un cuerpo de función, del que solo se puede salir mediante una instrucción return o llegando al final del bloque.  
  
 El ejemplo siguiente genera la advertencia CS1632:  
  
```  
// CS1632.cs // compile with: /target:library delegate void MyDelegate(); class MyClass { public void Test() { for (int i = 0 ; i < 5 ; i++) { MyDelegate d = delegate { break;   // CS1632 }; } } }  
```