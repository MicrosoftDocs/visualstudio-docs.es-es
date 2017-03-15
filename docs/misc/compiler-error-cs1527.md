---
title: "Error del compilador CS1527 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1527"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1527"
ms.assetid: a0d52130-d6da-41bb-b153-8e96cbb7e316
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1527
Los elementos definidos en un espacio de nombres no se pueden declarar explícitamente como private, protected o protected internal  
  
 Las declaraciones de tipos en un espacio de nombres pueden tener acceso de tipo [public](/dotnet/csharp/language-reference/keywords/public) o [internal](/dotnet/csharp/language-reference/keywords/internal). Si no se especifica la accesibilidad, el valor predeterminado es **internal**.  
  
 El ejemplo siguiente genera la advertencia CS1527:  
  
```  
// CS1527.cs namespace Sample { private class C1 {};             // CS1527 protected class C2 {};           // CS1527 protected internal class C3 {};  // CS1527 }  
```  
  
 El ejemplo siguiente genera el error CS1527 porque si no se declara ningún espacio de nombres explícitamente en el código de programa, todas las declaraciones de tipo se encuentran implícitamente en el espacio de nombres global.  
  
```  
//cs1527_2.cs using System; protected class C4{} private struct S1{}  
```  
  
## Vea también  
 [Espacios de nombres](/dotnet/csharp/programming-guide/namespaces/index)   
 [global](/dotnet/csharp/language-reference/keywords/global)   
 [:: \(operador\)](../Topic/::%20Operator%20\(C%23%20Reference\).md)   
 [Dominio de accesibilidad](/dotnet/csharp/language-reference/keywords/accessibility-domain)   
 [Modificadores de acceso](/dotnet/csharp/programming-guide/classes-and-structs/access-modifiers)