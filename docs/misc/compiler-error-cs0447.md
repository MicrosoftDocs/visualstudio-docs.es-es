---
title: "Error del compilador CS0447 | Microsoft Docs"
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
  - "CS0447"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0447"
ms.assetid: a25486c5-e9bf-4528-8533-c1aaab22ace0
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0447
Los atributos no se pueden utilizar en argumentos de tipo, sólo en parámetros de tipo  
  
 Este error se produce cuando se aplica un atributo a un argumento de tipo que se produce en una instrucción de invocación. Es aceptable aplicar un atributo a un parámetro de tipo en una instrucción de declaración de clase o método como la que se muestra a continuación:  
  
```  
class C<[some attribute] T> {…}  
```  
  
 La siguiente línea de código generará este error. Se supone que la clase `C`, definida en la línea anterior de código, tiene un método estático llamado `MyStaticMethod`.  
  
```  
C<[some attribute] T>.MyStaticMethod();  
```  
  
## Ejemplo  
 El código siguiente genera el error CS0447.  
  
```  
// CS0447.cs using System; namespace Test41 { public interface I<A> { void Meth<B>(); } public class B : I<int> { void I<[Test] int>.Meth<X>() { }  // CS0447 } }  
```