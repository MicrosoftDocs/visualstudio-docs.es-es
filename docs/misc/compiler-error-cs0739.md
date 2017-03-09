---
title: "Error del compilador CS0739 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0739"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0739"
ms.assetid: c2a83015-401c-4d85-bb19-ed29800904c1
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0739
Elemento TypeForwardedToAttribute duplicado en 'type name'.  
  
 Un ensamblado no puede tener más de un <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> en un tipo externo.  
  
### Para corregir este error  
  
1.  Localice y quite el <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> duplicado.  
  
## Ejemplo  
 El código siguiente genera el error CS0739:  
  
```  
// CS0739.cs // CS0739 // Assume that a class Test is declared in a separate dll // with a namespace that is named cs739dll. [assembly: System.Runtime.CompilerServices.TypeForwardedTo(typeof(cs739dll.Test))] [assembly: System.Runtime.CompilerServices.TypeForwardedTo(typeof(cs739dll.Test))] namespace cs0739 { class Program { static void Main(string[] args) { } } }  
```  
  
## Vea también  
 <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>