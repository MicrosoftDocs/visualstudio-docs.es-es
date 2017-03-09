---
title: "Error del compilador CS0473 | Microsoft Docs"
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
  - "CS0473"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0473"
ms.assetid: 58eb141e-7da0-41c8-b868-7cd2a15f07f9
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0473
La implementación de interfaz explícita 'nombre de método' coincide con más de un miembro de interfaz. El miembro de interfaz que se elige depende de la implementación. Considere el uso de una implementación no explícita en su lugar.  
  
 En algunos casos, un método genérico podría adquirir la misma signatura que un método no genérico. El problema es que en el sistema de metadatos de la infraestructura de lenguaje común \(en inglés, "Common Language Infrastructure" o CLI\)", no hay ninguna manera inequívoca de indicar qué método se enlaza a cada posición. Corresponde a CLI tomar esa determinación.  
  
> [!NOTE]
>  Este error se genera en Visual Studio 2008 en lugares donde no se produjo en Visual Studio 2005.  
  
### Para corregir este error  
  
1.  Elimine la implementación explícita y simplemente haga que la implementación implícita `public int TestMethod(int)` implementar ambos métodos de interfaz.  
  
## Ejemplo  
 El código siguiente genera el error CS0473:  
  
```  
// cs0473.cs public interface ITest<T> { int TestMethod(int i); int TestMethod(T i); } public class ImplementingClass : ITest<int> { int ITest<int>.TestMethod(int i) // CS0473 { return i + 1; } public int TestMethod(int i) { return i - 1; } } class T { static int Main() { ImplementingClass a = new ImplementingClass(); if (a.TestMethod(0) != -1) return -1; ITest<int> i_a = a; System.Console.WriteLine(i_a.TestMethod(0).ToString()); if (i_a.TestMethod(0) != 1) return -1; return 0; } }  
  
```  
  
## Vea también  
 [Fabulous Adventures in Coding](http://blogs.msdn.com/ericlippert/archive/2006/04/06/570126.aspx)