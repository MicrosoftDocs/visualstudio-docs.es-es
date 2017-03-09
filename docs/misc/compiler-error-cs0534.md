---
title: "Error del compilador CS0534 | Microsoft Docs"
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
  - "CS0534"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0534"
ms.assetid: 39fde9d1-3041-41fc-9dc2-43394c13c6c9
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0534
'function1' no implementa el miembro abstracto heredado 'function2'  
  
 Se necesita una clase para implementar todos los miembros [abstract](/dotnet/csharp/language-reference/keywords/abstract) de la clase base, a menos que la clase también sea abstract.  
  
 El ejemplo siguiente genera la advertencia CS0534:  
  
```  
// CS0534.cs namespace x { abstract public class clx { public abstract void f(); } public class cly : clx   // CS0534, no override for clx::f { // uncomment the following sample override to resolve CS0534 // override public void f() // { // } public static int Main() { return 0; } } }  
```