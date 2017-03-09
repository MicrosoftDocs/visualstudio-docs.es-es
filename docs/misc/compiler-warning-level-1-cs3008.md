---
title: "Advertencia del compilador (nivel 1) CS3008 | Microsoft Docs"
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
  - "CS3008"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3008"
ms.assetid: 593f6114-bc7b-4789-958f-97bbf99c1c9f
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 1) CS3008
El identificador 'identificador' que solo se diferencia por el uso de mayúsculas o minúsculas no es conforme a CLS  
  
 Un identificador [public](/dotnet/csharp/language-reference/keywords/public), [protected](/dotnet/csharp/language-reference/keywords/protected) o `protected` `internal` deja de ser conforme a Common Language Specification \(CLS\) si comienza con un guión bajo \(\_\). Para obtener más información sobre la conformidad con CLS, vea [Escribir código conforme a CLS](http://msdn.microsoft.com/es-es/4c705105-69a2-4e5e-b24e-0633bc32c7f3) y [Independencia del lenguaje y componentes independientes del lenguaje](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS3008:  
  
```  
// CS3008.cs using System; [assembly:CLSCompliant(true)] public class a { public static int _a = 0;  // CS3008 // OK, private // private static int _a1 = 0; public static void Main() { } }  
```