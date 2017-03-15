---
title: "Error del compilador CS1028 | Microsoft Docs"
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
  - "CS1028"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1028"
ms.assetid: 9df07db3-256f-45e9-8323-26539c55a1d8
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1028
Directiva de preprocesador inesperada  
  
 Se encontró una [directiva de preprocesador](/dotnet/csharp/language-reference/preprocessor-directives/index), pero no se esperaba.  
  
 Por ejemplo, se encontró un elemento `#endif` sin ningún elemento `#if` previo.  
  
 El ejemplo siguiente genera la advertencia CS1028:  
  
```  
// CS1028.cs #endif   // CS1028, no matching #if namespace x { public class clx { public static void Main() { } } }  
```