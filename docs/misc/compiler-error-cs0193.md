---
title: "Error del compilador CS0193 | Microsoft Docs"
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
  - "CS0193"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0193"
ms.assetid: 7b60fd99-9eee-4d61-ad75-585a16e22e96
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0193
El operador \* o \-\> se debe aplicar a un puntero  
  
 El operador **\*** o **\-\>** se usó con un tipo que no era de puntero. Para obtener más información, consulta [Tipos de puntero](/dotnet/csharp/programming-guide/unsafe-code-pointers/pointer-types).  
  
 El ejemplo siguiente genera la advertencia CS0193:  
  
```  
// CS0193.cs using System; public struct Age { public int AgeYears; public int AgeMonths; public int AgeDays; } public class MyClass { public static void SetAge(ref Age anAge, int years, int months, int days) { anAge->Months = 3;   // CS0193, anAge is not a pointer // try the following line instead // anAge.AgeMonths = 3; } public static void Main() { Age MyAge = new Age(); Console.WriteLine(MyAge.AgeMonths); SetAge(ref MyAge, 22, 4, 15); Console.WriteLine(MyAge.AgeMonths); } }  
```