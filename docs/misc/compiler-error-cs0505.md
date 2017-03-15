---
title: "Error del compilador CS0505 | Microsoft Docs"
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
  - "CS0505"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0505"
ms.assetid: e3cb9e33-7338-4869-859b-81d7439f0d23
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0505
'miembro1': no se puede reemplazar porque 'miembro2' no es una función.  
  
 Una declaración de clase intentó reemplazar un elemento que no es un método en una clase base. Los reemplazos deben coincidir en el tipo de miembro. Si quiere un método con el mismo nombre que un método en una clase base, use [new](/dotnet/csharp/language-reference/keywords/new) \(y no [override](/dotnet/csharp/language-reference/keywords/override)\) en la declaración del método en la clase base.  
  
 El ejemplo siguiente genera la advertencia CS0505:  
  
```  
// CS0505.cs // compile with: /target:library public class clx { public int i; } public class cly : clx { public override int i() { return 0; }   // CS0505 }  
```