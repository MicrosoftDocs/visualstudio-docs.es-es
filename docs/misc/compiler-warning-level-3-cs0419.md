---
title: "Advertencia del compilador (nivel 3) CS0419 | Microsoft Docs"
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
  - "CS0419"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0419"
ms.assetid: de439ad5-422f-4ed6-96d6-69dade29c7b2
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 3) CS0419
Referencia ambigua en el atributo cref: 'Method Name1'.  Se asume 'Method Name2', pero podría también coincidir con otras sobrecargas que incluyan 'Method Name3'.  
  
 En un comentario de documentación XML en el código, no se pudo resolver una referencia. Esto puede ocurrir si el método está sobrecargado, o si se encuentran dos identificadores diferentes con el mismo nombre. Para resolver la advertencia, use un nombre completo para eliminar la ambigüedad de la referencia, o incluya la sobrecarga concreta entre paréntesis.  
  
 El ejemplo siguiente genera la advertencia CS0419.  
  
```  
// cs0419.cs // compile with: /doc:x.xml /W:3 interface I { /// text for F(void) void F(); /// text for F(int) void F(int i); } /// text for class MyClass public class MyClass { /// <see cref="I.F"/> public static void MyMethod(int i) { } /* Try this instead: /// <see cref="I.F(int)"/> public static void MyMethod(int i) { } */ /// text for Main public static void Main () { } }  
```