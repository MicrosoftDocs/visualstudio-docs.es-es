---
title: "Error del compilador CS1038 | Microsoft Docs"
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
  - "CS1038"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1038"
ms.assetid: 05c53ae9-2819-4771-aee8-3f2ff6bcf0b0
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1038
Se esperaba la directiva \#endregion  
  
 Una directiva [\#region](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-region) no tenía una directiva [\#endregion](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-endregion) coincidente.  
  
 El ejemplo siguiente genera la advertencia CS1038:  
  
```  
// CS1038.cs #region testing public class clx { public static void Main() { } } // CS1038 // uncomment the next line to resolve // #endregion  
```