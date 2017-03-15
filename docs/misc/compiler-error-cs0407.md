---
title: "Error del compilador CS0407 | Microsoft Docs"
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
  - "CS0407"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0407"
ms.assetid: 59112fb9-4641-466e-b738-b3228539a09e
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0407
'método de tipo de valor devuelto' tiene un tipo de valor devuelto incorrecto  
  
 El método no es compatible con el tipo delegado. Los tipos de argumento coinciden, pero el tipo de valor devuelto no es el correcto para ese delegado. Para evitar este error, use otro método, cambie el tipo de valor devuelto del método o cambie el tipo de valor devuelto del delegado.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0407:  
  
```  
// CS0407.cs public delegate int MyDelegate(); class C { MyDelegate d; public C() { d = new MyDelegate(F);  // OK: F returns int d = new MyDelegate(G);  // CS0407 – G doesn't return int } public int F() { return 1; } public void G() { } public static void Main() { C c1 = new C(); } }  
```