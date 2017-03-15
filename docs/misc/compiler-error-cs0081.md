---
title: "Error del compilador CS0081 | Microsoft Docs"
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
  - "CS0081"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0081"
ms.assetid: a5649abc-89ea-4f64-8c3c-eb36df926561
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0081
La declaración de parámetros de tipo debe ser un identificador, no un tipo  
  
 Cuando declare un tipo o método genérico, especifique el parámetro de tipo como un identificador, por ejemplo, "T" o "inputType". Cuando el código de cliente llama al método, proporciona el tipo, que reemplaza cada aparición del identificador en el cuerpo del método o la clase. Para obtener más información, consulta [Parámetros de tipos genéricos](/dotnet/csharp/programming-guide/generics/generic-type-parameters).  
  
```  
// CS0081.cs class MyClass { public void F<int>() {}   // CS0081 public void F<T>(T input) {}   // OK public static void Main() { MyClass a = new MyClass(); a.F<int>(2); a.F<double>(.05); } }  
```  
  
## Vea también  
 [Genéricos](/dotnet/csharp/programming-guide/generics/index)