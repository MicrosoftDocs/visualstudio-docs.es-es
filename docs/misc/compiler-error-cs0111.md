---
title: "Error del compilador CS0111 | Microsoft Docs"
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
  - "CS0111"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0111"
ms.assetid: 87afb689-f27b-451d-84eb-d6bdf17aea41
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0111
El tipo 'class' ya define un miembro denominado 'member' con los mismos tipos de parámetros  
  
 CS0111 se produce si una clase contiene dos declaraciones de miembro con el mismo nombre y los mismos tipos de parámetros. Para obtener más información, consulta [Métodos](/dotnet/csharp/programming-guide/classes-and-structs/methods).  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0111.  
  
```  
// CS0111.cs class A { void Test() { } public static void Test(){}   // CS0111 public static void Main() {} }  
```