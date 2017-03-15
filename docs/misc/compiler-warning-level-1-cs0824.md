---
title: "Advertencia del compilador (nivel 1) CS0824 | Microsoft Docs"
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
  - "CS0824"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0824"
ms.assetid: ad643bb7-51b2-455b-a9f3-2bd4588d2c5d
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 1) CS0824
El constructor 'name' está marcado como externo.  
  
 Un constructor puede marcarse como extern. Sin embargo, el compilador no puede comprobar que existe realmente el constructor. Por lo tanto, se genera la advertencia.  
  
### Para quitar esta advertencia  
  
1.  Utilice una directiva de advertencia pragma para omitirla.  
  
2.  Mueva el constructor dentro del tipo.  
  
## Ejemplo  
 El código siguiente genera CS0824:  
  
```  
// cs0824.cs public class C { extern C(); // CS0824 public static int Main() { return 1; } }  
```  
  
## Vea también  
 [extern](/dotnet/csharp/language-reference/keywords/extern)   
 [\#pragma warning](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning)