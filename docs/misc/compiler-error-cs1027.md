---
title: "Error del compilador CS1027 | Microsoft Docs"
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
  - "CS1027"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1027"
ms.assetid: a6657f0f-5664-47a5-95cf-803f5a0e0c90
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1027
Se esperaba la directiva \#endif  
  
 No se encontró ninguna coincidencia de `#endif` [directiva de preprocesador](/dotnet/csharp/language-reference/preprocessor-directives/index) para una directiva `#if`especificada. O bien, es posible que el compilador haya encontrado una directiva `#endregion` cuando no había ninguna directiva `#region` coincidente dentro de un bloque `#if`.  
  
 El ejemplo siguiente genera la advertencia CS1027:  
  
```  
// CS1027.cs #if true   // CS1027, uncomment next line to resolve // #endif namespace x { public class clx { public static void Main() { } } }  
```