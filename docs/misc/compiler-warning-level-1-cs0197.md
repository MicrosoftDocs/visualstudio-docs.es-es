---
title: "Advertencia del compilador (nivel 1) CS0197 | Microsoft Docs"
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
  - "CS0197"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0197"
ms.assetid: 2b5b1b8d-ce13-4bd7-b80a-abb80e9f79ad
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 1) CS0197
No se puede pasar 'argumento' como out o ref ni usar su dirección porque podría provocar una excepción en tiempo de ejecución ya que es un campo de una clase de cálculo por referencia  
  
 Cualquier clase que se deriva, directa o indirectamente, de <xref:System.MarshalByRefObject> es una clase de cálculo por referencia. Esta clase se puede calcular por referencia sin tener en cuenta los límites de proceso o equipo. Por ello, las instancias de esta clase pueden ser proxy respecto de objetos remotos. No se puede pasar un campo de un objeto proxy como [out](/dotnet/csharp/language-reference/keywords/out) o [ref](/dotnet/csharp/language-reference/keywords/ref). Por lo tanto, no se pueden pasar los campos de dicha clase como `out` o `ref`, a menos que la instancia sea [this](/dotnet/csharp/language-reference/keywords/this), que no puede ser un objeto proxy.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0197.  
  
```  
// CS0197.cs // compile with: /W:1 class X : System.MarshalByRefObject { public int i; } class M { public int i; static void AddSeventeen(ref int i) { i += 17; } static void Main() { X x = new X(); x.i = 12; AddSeventeen(ref x.i);   // CS0197 // OK M m = new M(); m.i = 12; AddSeventeen(ref m.i); } }  
```