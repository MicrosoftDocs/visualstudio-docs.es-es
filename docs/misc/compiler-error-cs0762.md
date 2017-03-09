---
title: "Error del compilador CS0762 | Microsoft Docs"
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
  - "CS0762"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0762"
ms.assetid: 7cedd1af-ffe6-4ca7-82fb-faa9e98014a4
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0762
No se puede crear un delegado a partir del método 'method' porque es un método parcial sin una declaración de implementación  
  
 No se necesita un método parcial para tener una declaración de implementación. Sin embargo, un delegado requiere que su método encapsulado tenga una implementación.  
  
### Para corregir este error  
  
1.  Proporcione una implementación para el método usado para inicializar el delegado.  
  
## Ejemplo  
  
```  
public delegate void TestDel(); public partial class C { partial void Part(); public static int Main() { C c = new C(); TestDel td = new TestDel(c.Part); // CS0762 return 1; } }  
```