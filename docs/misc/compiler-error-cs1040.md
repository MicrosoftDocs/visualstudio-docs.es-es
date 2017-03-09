---
title: "Error del compilador CS1040 | Microsoft Docs"
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
  - "CS1040"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1040"
ms.assetid: a988d665-ead5-489f-922d-ff2c4dd8a922
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1040
Las directivas de preprocesador deben ser el primer carácter de una línea que no sea un espacio en blanco  
  
 Se encontró una [directiva de preprocesador](/dotnet/csharp/language-reference/preprocessor-directives/index) en una línea y no era el primer símbolo de la línea. Una directiva debe ser el primer símbolo de la línea.  
  
 El ejemplo siguiente genera la advertencia CS1040:  
  
```  
// CS1040.cs /* Define a symbol, X */ #define X   // CS1040 // try the following two lines instead // /* Define a symbol, X */ // #define X public class MyClass { public static void Main() { } }  
```