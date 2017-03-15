---
title: "Error del compilador CS0685 | Microsoft Docs"
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
  - "CS0685"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0685"
ms.assetid: 20d7c6cf-a388-430f-b22b-232536912491
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0685
El miembro condicional 'member' no puede tener ningún parámetro out  
  
 Cuando se usa el atributo <xref:System.Diagnostics.ConditionalAttribute> en un método, es posible que dicho método no tenga un parámetro out. Esto se debe a que el valor de la variable usada para el parámetro out no estaría definiría en caso de que la llamada de método estuviese compilada en nada. Para evitar este error, quite el parámetro out de la declaración de método condicional o no use el atributo Conditional.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0685:  
  
```  
// CS0685.cs using System.Diagnostics; class C { [Conditional("DEBUG")] void trace(out int i)  // CS0685 { i = 1; } }  
```