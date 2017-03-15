---
title: "Error del compilador CS0756 | Microsoft Docs"
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
  - "CS0756"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0756"
ms.assetid: 847b20b0-bbf0-43a2-8728-4b54cb3d9cd6
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0756
Un método parcial no puede tener varias declaraciones de definición.  
  
 La declaración de definición de un método parcial es la parte que especifica la firma del método, pero no la implementación \(cuerpo del método\). Un método parcial debe tener exactamente una declaración de definición para cada firma única. Cada versión sobrecargada de un método parcial debe tener su propia declaración de definición.  
  
### Para corregir este error  
  
1.  Quite todas las declaraciones de definición del método parcial, excepto una.  
  
## Ejemplo  
  
```  
// cs0756.cs using System; public partial class C { partial void Part(); partial void Part(); // CS0756 public static int Main() { return 1; } }  
```  
  
## Vea también  
 [Clases y métodos parciales](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)