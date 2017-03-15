---
title: "Error del compilador CS0764 | Microsoft Docs"
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
  - "CS0764"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0764"
ms.assetid: 76a64149-49d8-40ea-a976-03835d8fb7eb
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0764
Ambas declaraciones de métodos parciales deben ser no seguras o ninguna de ellas puede ser no segura  
  
 Un método parcial consta de una declaración de definición \(signatura\) y una declaración de implementación opcional \(cuerpo\). Si la declaración de definición contiene el modificador `unsafe`, la declaración de implementación también debe tenerlo. A la inversa, si la declaración de implementación contiene el modificador `unsafe`, la declaración de definición también debe tenerlo.  
  
### Para corregir este error  
  
1.  Suponiendo que la declaración de definición sea correcta, agregue o quite el modificador `unsafe` de la declaración de implementación para que coincida con la declaración de definición.  
  
## Ejemplo  
  
```  
// cs0764.cs //  Compile with: /target:library /unsafe public partial class C { partial void Part(); unsafe partial void Part() //CS0764 { } public static int Main() { return 1; } }  
```  
  
## Vea también  
 [Clases y métodos parciales](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)