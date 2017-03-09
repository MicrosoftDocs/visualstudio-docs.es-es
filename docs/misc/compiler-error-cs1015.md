---
title: "Error del compilador CS1015 | Microsoft Docs"
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
  - "CS1015"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1015"
ms.assetid: 53179feb-e8be-41e0-bb0b-f7879e9fa613
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1015
Un objeto, una cadena o un tipo de clase esperados  
  
 Se intentó pasar un tipo de datos predefinido en un bloque [catch](/dotnet/csharp/language-reference/keywords/try-catch). Solo los tipos de datos que se derivan de <xref:System.Exception?displayProperty=fullName> se pueden pasar en un bloque `catch`. Para más información sobre excepciones, vea [Instrucciones para el control de excepciones](/dotnet/csharp/language-reference/keywords/exception-handling-statements).  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS1015:  
  
```  
// CS1015.cs class Sample { static void Main() { try { } catch(int)   // CS1015, int is not derived from System.Exception { } } }  
```