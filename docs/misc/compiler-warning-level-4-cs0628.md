---
title: "Advertencia del compilador (nivel 4) CS0628 | Microsoft Docs"
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
  - "CS0628"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0628"
ms.assetid: a54cfad8-27c9-4abb-8c83-982615489a10
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 4) CS0628
'member': nuevo miembro protegido declarado en la clase sealed  
  
 Una clase [sealed](/dotnet/csharp/language-reference/keywords/sealed) no puede introducir un miembro [protected](/dotnet/csharp/language-reference/keywords/protected) porque ninguna otra clase podría heredar de la clase `sealed` y usar el miembro `protected`.  
  
 El ejemplo siguiente genera la advertencia CS0628:  
  
```  
// CS0628.cs // compile with: /W:4 sealed class C { protected int i;   // CS0628 } class MyClass { public static void Main() { } }  
```