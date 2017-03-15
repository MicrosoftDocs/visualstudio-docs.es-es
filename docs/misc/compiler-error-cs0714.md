---
title: "Error del compilador CS0714 | Microsoft Docs"
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
  - "CS0714"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0714"
ms.assetid: fbb5dc55-645c-4980-bf4b-3c2f84a3c6cd
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0714
'tipo estático': las clases estáticas no pueden implementar interfaces.  
  
 Las interfaces pueden definir métodos no estáticos en objetos y, por tanto, no se pueden implementar mediante clases estáticas. Para resolver este error, asegúrese de que su clase no intenta implementar ninguna interfaz.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0714:  
  
```  
// CS0714.cs interface I { } public static class C : I  // CS0714 { public static void Main() { } }  
```