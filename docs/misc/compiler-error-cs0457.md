---
title: "Error del compilador CS0457 | Microsoft Docs"
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
  - "CS0457"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0457"
ms.assetid: 5d5cf762-c817-4468-9455-59e966b8c140
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0457
Conversiones ambiguas 'Nombre de método de conversión 1' y 'Nombre de método de conversión 2' definidas por el usuario al realizar la conversión de 'nombre de tipo 1' a 'nombre de tipo 2'  
  
 Dos métodos de conversión son aplicables, pero el compilador no puede decidir cuál usar.  
  
 Un escenario que puede generar este error es el siguiente:  
  
-   Quiere convertir la clase A a la clase B, donde A y B no están relacionadas.  
  
-   A se deriva de A0 y hay un método que convierte de A0 a B.  
  
-   B tiene una subclase B1 y hay un método que convierte de A a B1.  
  
 El compilador ponderará ambos métodos de conversión por igual, porque la primera conversión ofrece el mejor tipo de destino y la segunda conversión ofrece el mejor tipo de origen. Puesto que el compilador no podrá elegir, se generará este error. Para resolverlo, escriba un nuevo método explícito para efectuar la conversión de A a B.  
  
 Otro escenario que provoca este error es la existencia de dos métodos que convierten A a B. Para solucionarlo, especifique qué conversión se debe usar mediante una conversión explícita.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0457.  
  
```  
// CS0457.cs using System; public class A { } public class G0 {  } public class G1<R> : G0 {  } public class H0 { public static implicit operator G0(H0 h) { return new G0(); } } public class H1<R> : H0 { public static implicit operator G1<R>(H1<R> h) { return new G1<R>(); } } public class Test { public static void F0(G0 g) {  } public static void Main() { H1<A> h1a = new H1<A>(); F0(h1a);   // CS0457 } }  
```