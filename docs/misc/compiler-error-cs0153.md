---
title: "Error del compilador CS0153 | Microsoft Docs"
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
  - "CS0153"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0153"
ms.assetid: 3a0791e9-0ab9-4eaa-a230-d39aabaa9d5d
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0153
Una instrucción goto case solo es válida dentro de una instrucción switch  
  
 Se intentó usar la sintaxis [switch](/dotnet/csharp/language-reference/keywords/switch) fuera de una instrucción **switch**. Para obtener más información, consulta [switch](/dotnet/csharp/language-reference/keywords/switch).  
  
 El ejemplo siguiente genera la advertencia CS0153:  
  
```  
// CS0153.cs public class a { public static void Main() { goto case 5;   // CS0153 } }  
```