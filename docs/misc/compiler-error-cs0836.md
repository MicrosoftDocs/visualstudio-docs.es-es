---
title: "Error del compilador CS0836 | Microsoft Docs"
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
  - "CS0836"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0836"
ms.assetid: 74a12271-1612-45aa-a398-7964e0269892
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0836
No se puede usar un tipo anónimo en una expresión constante.  
  
 Lo único que se permite en una expresión de constante son las constantes denominadas, los literales y las expresiones matemáticas que combinan expresiones constantes.  
  
### Para corregir este error  
  
1.  Convierta un tipo con nombre al tipo anónimo.  
  
## Ejemplo  
 En el siguiente ejemplo, se muestra una forma de generar el error CS0836:  
  
```  
// cs0836.cs using System; [AttributeUsage(AttributeTargets.Class, AllowMultiple = true, Inherited = false)] public class A : Attribute { public A(object obj) { } } [A(new { })] // CS0836 public class B { } public class Test { public static int Main() { return 0; } }  
```