---
title: "Error del compilador CS0664 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0664"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0664"
ms.assetid: 60fe15a7-db22-414f-a7b8-fac79dad22b4
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0664
El literal de tipo double no se puede convertir implícitamente al tipo 'tipo'. Use un sufijo 'sufijo' para crear un literal de este tipo  
  
 No se puede completar una asignación. Use un sufijo para corregir la instrucción. La documentación de cada tipo identifica el sufijo que le corresponde. Para obtener más información sobre las conversiones, vea [Conversiones de tipos](/dotnet/csharp/programming-guide/types/casting-and-type-conversions).  
  
 El ejemplo siguiente genera la advertencia CS0664:  
  
```c#  
// CS0664.cs class Example { static void Main() { decimal d1 = 1.0;   // CS0664, because 1.0 is interpreted // as a double. // Try the following line instead. decimal d2 = 1.0M;  // The M tells the compiler that 1.0 is a // decimal. Console.WriteLine(d2); } }  
```  
  
## Vea también  
 [Tablas de conversión de tipos](../Topic/Type%20Conversion%20Tables%20in%20the%20.NET%20Framework.md)