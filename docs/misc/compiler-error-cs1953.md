---
title: "Error del compilador CS1953 | Microsoft Docs"
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
  - "CS1953"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1953"
ms.assetid: b8af5eed-0f3b-4258-b4e2-f5d184288239
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1953
Una lambda de árbol de expresión podría no contener un grupo de métodos.  
  
 Una llamada de método requiere el operador `()`. El nombre del método sin ese operador hace referencia al grupo de métodos, que es el conjunto de todos los métodos sobrecargados con ese nombre.  
  
### Para corregir este error  
  
1.  Para llamar al método, agregue el operador `()`.  
  
## Ejemplo  
 El siguiente ejemplo genera el error CS1953:  
  
```  
// cs1953.cs using System; using System.Linq.Expressions; class CS1953 { public static void Main() { double num = 10; Expression<Func<bool>> testExpr = () => num.GetType is int; // CS1953 } }  
```