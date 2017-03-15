---
title: "Error del compilador CS1657 | Microsoft Docs"
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
  - "CS1657"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1657"
ms.assetid: 6f0aeebe-5c90-4d5b-981c-1795d2e8fbb9
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1657
No se puede pasar 'parameter' como argumento out o ref porque es 'reason'  
  
 Este error se produce cuando se pasa una variable como argumento [ref](/dotnet/csharp/language-reference/keywords/ref) o [out](/dotnet/csharp/language-reference/keywords/out) en un contexto en el que dicha variable es de solo lectura. Los contextos de solo lectura incluyen las variables de iteración [foreach](/dotnet/csharp/language-reference/keywords/foreach-in), variables [using](/dotnet/csharp/language-reference/keywords/using-statement) y variables `fixed`. Para resolver este error, no llame a las funciones que toman la variable `foreach`, `using` o `fixed` como parámetro `ref` o `out` en bloques `using`, instrucciones `foreach` e instrucciones `fixed`.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS1657:  
  
```  
// CS1657.cs using System; class C : IDisposable { public int i; public void Dispose() {} } class CMain { static void f(ref C c) { } static void Main() { using (C c = new C()) { f(ref c);  // CS1657 } } }  
```  
  
## Ejemplo  
 El código siguiente ilustra el mismo problema en una instrucción `fixed`:  
  
```  
// CS1657b.cs // compile with: /unsafe unsafe class C { static void F(ref int* p) { } static void Main() { int[] a = new int[5]; fixed(int* p = a) F(ref p); // CS1657 } }  
```