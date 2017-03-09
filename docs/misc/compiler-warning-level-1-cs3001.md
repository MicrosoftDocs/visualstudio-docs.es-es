---
title: "Advertencia del compilador (nivel 1) CS3001 | Microsoft Docs"
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
  - "CS3001"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3001"
ms.assetid: c4f3e247-5e47-4182-b415-c573fb1a152f
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 1) CS3001
El tipo de argumento 'type' no cumple con CLS  
  
 Un método [public](/dotnet/csharp/language-reference/keywords/public), [protected](/dotnet/csharp/language-reference/keywords/protected) o `protected` `internal` debe aceptar un parámetro que tenga un tipo conforme con Common Language Specification \(CLS\). Para más información sobre la conformidad con CLS, vea [Escribir código conforme con CLS](http://msdn.microsoft.com/es-es/4c705105-69a2-4e5e-b24e-0633bc32c7f3) y [Independencia del lenguaje y componentes independientes del lenguaje](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS3001:  
  
```  
// CS3001.cs [assembly:System.CLSCompliant(true)] public class a { public void bad(ushort i)   // CS3001 { } private void OK(ushort i)   // OK, private method { } public static void Main() { } }  
```