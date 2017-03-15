---
title: "Error del compilador CS0746 | Microsoft Docs"
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
  - "CS0746"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0746"
ms.assetid: 36baf7f2-b092-422c-ab53-95154bfceb0a
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0746
Declarador de miembro de tipo anónimo no válido. Los miembros de tipo anónimo deben declararse con una asignación de miembro, un nombre simple o un acceso al miembro.  
  
 Un tipo anónimo debe declararse con una asignación de miembro, un nombre simple o un acceso a miembro.  
  
### Para corregir este error  
  
1.  Asegúrese de que la declaración solo usa asignación de miembro, nombres simples o expresiones de acceso a miembros.  
  
## Ejemplo  
 El código siguiente genera el error CS0746 en la declaración de `incorrect_1` y `incorrect_2`. Las declaraciones siguientes son dos de las formas correctas para declarar un tipo anónimo.  
  
```  
// cs0746.cs public class C { public static int Main() { int i = 100; string s = "Bottles of beer."; var incorrect_1 = new { a.b = 1 }; // CS0746 var incorrect_2 = new {100, "Bottles of beer."}; // CS0746 var correct_1 = new { i, s }; //OK var correct_2 = new {num = i, message = s}; // OK return 1; } }  
  
```  
  
## Vea también  
 [Tipos anónimos](/dotnet/csharp/programming-guide/classes-and-structs/anonymous-types)