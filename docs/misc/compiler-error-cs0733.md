---
title: "Error del compilador CS0733 | Microsoft Docs"
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
  - "CS0733"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0733"
ms.assetid: 1b0150e0-48d3-4b9c-85cc-27346e4f5f84
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0733
No se puede reenviar el tipo genérico, 'GenericType\<\>'  
  
## Ejemplo  
 El siguiente ejemplo genera el error CS0733. Compile el primer archivo como una biblioteca y, después, haga referencia a este cuando compile el segundo archivo.  
  
```  
// CS0733a.cs // compile with: /target:library public class GenericType<T> { }  
```  
  
```  
// CS0733.cs // compile with: /target:library /r:CS0733a.dll [assembly: System.Runtime.CompilerServices.TypeForwardedTo(typeof(GenericType<int>))]   // CS0733  
```