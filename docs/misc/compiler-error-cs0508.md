---
title: "Error del compilador CS0508 | Microsoft Docs"
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
  - "CS0508"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0508"
ms.assetid: 28403573-6e64-4496-918d-fb50c8851e51
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0508
'Tipo 1': el tipo de valor devuelto debe ser 'Tipo 2' para que coincida con el miembro reemplazado 'Nombre de miembro'  
  
 Se ha intentado cambiar el tipo de valor devuelto en un reemplazo de método. Para resolver este error, asegúrese de que ambos métodos declaren el mismo tipo de valor devuelto.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0508.  
  
```  
// CS0508.cs // compile with: /target:library abstract public class Clx { public int i = 0; // Return type is int. abstract public int F(); } public class Cly : Clx { public override double F() { return 0.0;   // CS0508 } }  
```