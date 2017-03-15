---
title: "Error del compilador CS1025 | Microsoft Docs"
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
  - "CS1025"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1025"
ms.assetid: 491c186f-cb40-47a9-9656-44fadfa18ae2
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1025
Se esperaba un comentario de una línea o un fin de línea  
  
 Una línea con una [directiva de preprocesador](/dotnet/csharp/language-reference/preprocessor-directives/index) no puede tener un comentario multilínea.  
  
 El ejemplo siguiente genera la advertencia CS1025:  
  
```  
#if true /* hello */   // CS1025 #endif   // this is a good comment  
```  
  
 El error CS1025 también puede producirse si se intenta alguna directiva de preprocesador no válida, como se indica a continuación:  
  
```  
// CS1025.cs #define a class Sample { static void Main() { #if a 1   // CS1025, invalid syntax System.Console.WriteLine("Hello, World!"); #endif } }  
```