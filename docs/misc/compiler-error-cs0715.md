---
title: "Error del compilador CS0715 | Microsoft Docs"
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
  - "CS0715"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0715"
ms.assetid: e3cd1e46-ccfa-4678-a2ed-69245f3558ba
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0715
'clase estática': las clases estáticas no pueden contener operadores definidos por el usuario.  
  
 Los operadores definidos por el usuario funcionan en instancias de clases. No se pueden crear instancias de clases estáticas, por lo que no es posible crear instancias en las que los operadores puedan actuar. Por lo tanto, no se permiten operadores definidos por el usuario para clases estáticas.  
  
 El ejemplo siguiente genera la advertencia CS0715:  
  
```  
// CS0715.cs public static class C { public static C operator+(C c)  // CS0715 { } public static void Main() { } }  
```