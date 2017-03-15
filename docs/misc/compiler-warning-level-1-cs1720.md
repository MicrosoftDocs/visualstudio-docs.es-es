---
title: "Advertencia del compilador (nivel 1) CS1720 | Microsoft Docs"
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
  - "CS1720"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1720"
ms.assetid: 97adc294-3a4c-4418-a4ed-ccff43125b62
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 1) CS1720
La expresión siempre producirá la excepción System.NullReferenceException porque el valor predeterminado de 'tipo genérico' es null  
  
 Si escribe una expresión que contiene el valor predeterminado de una variable de tipo genérico que es un tipo de referencia \(por ejemplo, una clase\), se producirá este error. Observe la siguiente expresión:  
  
```  
default(T).ToString()  
```  
  
 Puesto que `T` es un tipo de referencia, su valor predeterminado es null y al intentar aplicarle el método <xref:System.Object.ToString%2A>, producirá una excepción <xref:System.NullReferenceException>.  
  
## Ejemplo  
 La restricción de referencia de clase en el tipo `T` garantiza que `T` es un tipo de referencia.  
  
 El ejemplo siguiente genera la advertencia CS1720.  
  
```  
// CS1720.cs using System; public class Tester { public static void GenericClass<T>(T t1) where T : class { Console.WriteLine(default(T).ToString());  // CS1720 } public static void Main() {} }  
```