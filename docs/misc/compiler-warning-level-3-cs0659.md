---
title: "Advertencia del compilador (nivel 3) CS0659 | Microsoft Docs"
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
  - "CS0659"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0659"
ms.assetid: 63435ee6-c92f-4124-95d4-d8f4e5f0af80
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 3) CS0659
'clase' invalida Object.Equals\(object o\), pero no invalida Object.GetHashCode\(\)  
  
 El compilador detectó una invalidación de la función **Equals** pero no de **GetHashCode**. Una invalidación de **Equals** implica que también se quiere invalidar **GetHashCode**.  
  
 Para obtener más información, vea  
  
-   <xref:System.Collections.Hashtable>.  
  
-   [Operadores de igualdad](../Topic/Equality%20Operators.md)  
  
-   [NO ESTÁ EN LA COMPILACIÓN: Implementar el método Equals](http://msdn.microsoft.com/es-es/30f28aaf-8b9e-46cd-a746-58a12473af2c)  
  
-   <xref:System.Object.GetHashCode%2A>  
  
 El ejemplo siguiente genera la advertencia CS0659:  
  
```  
// CS0659.cs // compile with: /W:3 /target:library class Test { public override bool Equals(object o) { return true; }   // CS0659 } // OK class Test2 { public override bool Equals(object o) { return true; } public override int GetHashCode() { return 0; } }  
```