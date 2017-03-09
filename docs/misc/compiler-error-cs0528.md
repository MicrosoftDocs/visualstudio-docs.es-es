---
title: "Error del compilador CS0528 | Microsoft Docs"
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
  - "CS0528"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0528"
ms.assetid: 8f5dde55-7e4f-4ffa-be14-0e0f3a538118
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0528
'interfaz\!' ya aparece en la lista de interfaces.  
  
 Una lista de herencia de interfaces incluye un duplicado. Una [interfaz](/dotnet/csharp/language-reference/keywords/interface) solo puede especificarse una vez en la lista de herencia.  
  
 El ejemplo siguiente genera la advertencia CS0528:  
  
```  
// CS0528.cs namespace x { public interface a { } public class b : a, a   // CS0528 { public void Main() { } } }  
```