---
title: "Error del compilador CS1521 | Microsoft Docs"
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
  - "CS1521"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1521"
ms.assetid: 9a482b33-24f2-4654-81b4-be40bf56d624
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1521
Tipo base no válido  
  
 Hay especificación de clase [base](/dotnet/csharp/language-reference/keywords/base) con formato incorrecto.  
  
 El ejemplo siguiente genera la advertencia CS1521:  
  
```  
// CS1521.cs class CMyClass { public static void Main() { } } class CMyClass1 : CMyClass     // OK { } class CMyClass2 : CMyClass[]   // CS1521 { } class CMyClass3 : CMyClass*    // CS1521 { }  
```