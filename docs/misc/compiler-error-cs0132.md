---
title: "Error del compilador CS0132 | Microsoft Docs"
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
  - "CS0132"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0132"
ms.assetid: e8ad1281-2912-4b6a-b2af-a319a23ddd16
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0132
'constructor': un constructor static no debe tener parámetros.  
  
 Un constructor [static](/dotnet/csharp/language-reference/keywords/static) no se puede declarar con uno o más parámetros. Para obtener más información, consulta [Constructores](/dotnet/csharp/programming-guide/classes-and-structs/constructors).  
  
 El ejemplo siguiente genera la advertencia CS0132:  
  
```  
// CS0132.cs namespace MyNamespace { public class MyClass { public MyClass(int i) { } } public class MyClass2 : MyClass { static MyClass2(int i)   // CS0132 { } } }  
```