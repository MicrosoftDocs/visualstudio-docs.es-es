---
title: "Error del compilador CS1511 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1511"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1511"
ms.assetid: c04b5268-5bc3-41db-af6b-463ab1d802b4
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1511
La palabra clave 'base' no está disponible en ningún método estático  
  
 La palabra clave [base](/dotnet/csharp/language-reference/keywords/base) se usaba en un método [static](/dotnet/csharp/language-reference/keywords/static).`base` solo se puede llamar en un constructor de instancia, un método de instancia o un descriptor de acceso de instancia.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS1511.  
  
```  
// CS1511.cs // compile with: /target:library public class A { public int j = 0; } class C : A { public void Method() { base.j = 3;   // base allowed here } public static int StaticMethod() { base.j = 3;   // CS1511 return 1; } }  
```