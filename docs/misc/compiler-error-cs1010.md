---
title: "Error del compilador CS1010 | Microsoft Docs"
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
  - "CS1010"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1010"
ms.assetid: 3d47277a-253f-464b-a603-e3b37e0e7b0d
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1010
Nueva línea en constante  
  
 Una [cadena](/dotnet/csharp/language-reference/keywords/string) no se ha delimitado correctamente.  
  
 El ejemplo siguiente genera la advertencia CS1010:  
  
```  
// CS1010.cs class Sample { static void Main() { string a = "Hello World;   // CS1010 // Use the following line, with end quote before semicolon: string a = "Hello World"; // } }  
```  
  
## Vea también  
 [NIB \- Cadenas \(Guía de programación de C\#\)](http://msdn.microsoft.com/es-es/1a32b1c9-0d99-468a-9734-e3a47f2e897a)