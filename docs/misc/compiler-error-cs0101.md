---
title: "Error del compilador CS0101 | Microsoft Docs"
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
  - "CS0101"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0101"
ms.assetid: edb5246b-c16b-4845-bb2d-0ef769d014c7
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0101
El espacio de nombres 'namespace' ya contiene una definición de 'type'  
  
 Un [espacio de nombres](/dotnet/csharp/language-reference/keywords/namespace) tiene identificadores duplicados. Cambie el nombre o elimine uno de los identificadores duplicados. Para obtener más información, vea [Espacios de nombres](/dotnet/csharp/programming-guide/namespaces/index)  
  
 El ejemplo siguiente genera la advertencia CS0101:  
  
```  
// CS0101.cs namespace MyNamespace { public class MyClass { static public void Main() { } } public class MyClass   // CS0101 { } }  
```