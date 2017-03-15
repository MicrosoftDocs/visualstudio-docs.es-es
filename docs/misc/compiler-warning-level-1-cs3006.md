---
title: "Advertencia del compilador (nivel 1) CS3006 | Microsoft Docs"
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
  - "CS3006"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3006"
ms.assetid: efbfd898-e46f-4c3d-91e2-e2da0056b016
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 1) CS3006
El método sobrecargado 'method', que solo se diferencia en ref u out, o en el rango de matriz, no es conforme a CLS  
  
 Un método no se puede sobrecargar según el parámetro [ref](/dotnet/csharp/language-reference/keywords/ref) u [out](/dotnet/csharp/language-reference/keywords/out) y seguir siendo conforme a Common Language Specification \(CLS\). Para obtener más información sobre la conformidad con CLS, vea [Escribir código conforme a CLS](http://msdn.microsoft.com/es-es/4c705105-69a2-4e5e-b24e-0633bc32c7f3) y [Independencia del lenguaje y componentes independientes del lenguaje](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS3006. Para resolver esta advertencia, convierta en comentario el atributo de nivel de ensamblado o quite una de las definiciones de método.  
  
```  
// CS3006.cs using System; [assembly: CLSCompliant(true)] public class MyClass { public void f(int i) { } public void f(ref int i)   // CS3006 { } public static void Main() { } }  
```