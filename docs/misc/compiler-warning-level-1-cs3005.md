---
title: "Advertencia del compilador (nivel 1) CS3005 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS3005"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3005"
ms.assetid: 64b687e3-2dbd-45dd-b6da-81f77eb7d6bd
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 1) CS3005
El identificador 'identifier' solo es distinto si no es conforme con CLS  
  
 Un identificador [public](/dotnet/csharp/language-reference/keywords/public), [protected](/dotnet/csharp/language-reference/keywords/protected) o `protected` `internal` que difiera de otro identificador `public`, `protected` o `protected` `internal` solo en el caso de una o varias letras, no es compatible con Common Language Specification \(CLS\). Para más información sobre la conformidad con CLS, vea [Escribir código conforme con CLS](http://msdn.microsoft.com/es-es/4c705105-69a2-4e5e-b24e-0633bc32c7f3) y [Independencia del lenguaje y componentes independientes del lenguaje](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS3003:  
  
```  
// CS3005.cs using System; [assembly:CLSCompliant(true)] public class a { public static int a1 = 0; public static int A1 = 1;   // CS3005 public static void Main() { Console.WriteLine(a1); Console.WriteLine(A1); } }  
```