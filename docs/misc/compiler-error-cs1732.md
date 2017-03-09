---
title: "Error del compilador CS1732 | Microsoft Docs"
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
  - "CS1732"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1732"
ms.assetid: 72c7f7fc-d5f2-4538-9b02-50dda54d3b1e
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1732
Se esperaba un parámetro.  
  
 Este error se produce cuando una expresión lambda contiene una coma después de un parámetro de entrada, pero no especifica el parámetro siguiente.  
  
### Para corregir este error  
  
1.  Quite la coma o agregue el parámetro de entrada que el compilador espera encontrar después de la coma.  
  
## Ejemplo  
 El siguiente ejemplo genera el error CS1732:  
  
```  
// cs1732.cs // compile with: /target:library class Test { delegate void D(int x, int y); static void Main() { D d = (x,) => { }; // CS1732 } }  
```