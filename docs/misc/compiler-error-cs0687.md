---
title: "Error del compilador CS0687 | Microsoft Docs"
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
  - "CS0687"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0687"
ms.assetid: b51c5e7c-f4de-4aa4-97b1-ebe220cd19b0
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0687
El calificador de alias del espacio de nombres '::' siempre se resuelve en un tipo o espacio de nombres, por tanto, aquí no es válido. Considere usar '.' en su lugar.  
  
 Este error se produce si ha usado algo que el analizador ha interpretado como un tipo en un lugar inesperado. Un nombre de tipo o espacio de nombres solo es válido en una expresión de acceso de miembro, con el operador de acceso de miembro \(**.**\). Esto puede ocurrir si usa el operador de ámbito global \(::\) en otro contexto.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0687:  
  
```  
// CS0687.cs using M = Test; using System; public class Test { public static int x = 77; public static void Main() { Console.WriteLine(M::x); // CS0687 // To resolve use the following line instead: // Console.WriteLine(M.x); } }  
```