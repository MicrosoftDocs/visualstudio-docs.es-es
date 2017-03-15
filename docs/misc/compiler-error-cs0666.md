---
title: "Error del compilador CS0666 | Microsoft Docs"
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
  - "CS0666"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0666"
ms.assetid: 44ad4574-b4a2-487b-8d05-0116762231ab
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0666
'miembro': nuevo miembro protegido declarado en struct  
  
 Una [struct](/dotnet/csharp/language-reference/keywords/struct) no puede ser [abstract](/dotnet/csharp/language-reference/keywords/abstract) y siempre es [sealed](/dotnet/csharp/language-reference/keywords/sealed) implícitamente. Dado que las estructuras no admiten la herencia, el concepto de un miembro [protected](/dotnet/csharp/language-reference/keywords/protected) de una estructura no tiene sentido. Para obtener más información, consulta [Herencia](/dotnet/csharp/programming-guide/classes-and-structs/inheritance).  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0666:  
  
```  
// CS0666.cs class M { static void Main() { } } struct S { protected int x;   // CS0666 }  
```