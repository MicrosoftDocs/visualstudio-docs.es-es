---
title: "Error del compilador CS0058 | Microsoft Docs"
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
  - "CS0058"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0058"
ms.assetid: 9535da60-03b9-41ab-93e1-e57b6440fca9
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0058
Incoherencia de accesibilidad: el tipo de valor devuelto 'tipo' es menos accesible que el delegado 'delegado'.  
  
 Una construcción pública debe devolver un objeto accesible públicamente. Para obtener más información, consulta [Modificadores de acceso](/dotnet/csharp/programming-guide/classes-and-structs/access-modifiers).  
  
 El ejemplo siguiente genera la advertencia CS0058 porque no se aplica ningún modificador de acceso a MyClass y, por tanto, tiene de forma predeterminada accesibilidad privada:  
  
```  
// CS0058.cs class MyClass // try the following line instead // public class MyClass { } public delegate MyClass MyClassDel();   // CS0058 public class A { public static void Main() { } }  
```  
  
## Vea también  
 [private](/dotnet/csharp/language-reference/keywords/private)