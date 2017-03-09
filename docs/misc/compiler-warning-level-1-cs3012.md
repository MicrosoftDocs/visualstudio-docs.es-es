---
title: "Advertencia del compilador (nivel 1) CS3012 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS3012"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3012"
ms.assetid: 1f7555b4-61e4-4821-85c9-586301df4c5c
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 1) CS3012
No se puede especificar el atributo CLSCompliant en un módulo que sea distinto del atributo CLSCompliant del ensamblado  
  
 Para que un módulo sea conforme a Common Language Specification \(CLS\) a través de `[module:System.CLCSompliant(true)]`, debe compilarse con la opción del compilador [\/target:module](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md). Para más información sobre CLS, vea [Independencia del lenguaje y componentes independientes del lenguaje](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).  
  
## Ejemplo  
 En el ejemplo siguiente, al realizar la compilación sin `/target:module`, se genera la advertencia CS3012:  
  
```  
// CS3012.cs // compile with: /W:1 [module:System.CLSCompliant(true)]   // CS3012 public class C { public static void Main() { } }  
```