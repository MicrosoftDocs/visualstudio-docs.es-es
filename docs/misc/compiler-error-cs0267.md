---
title: "Error del compilador CS0267 | Microsoft Docs"
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
  - "CS0267"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0267"
ms.assetid: 11aaab96-5838-4e36-9551-5b032a1089e1
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0267
El modificador 'partial' solo puede aparecer inmediatamente antes de 'class', 'struct' o 'interface'  
  
 La colocación del modificador **partial** era incorrecta en la declaración de la clase, el struct o la interfaz. Para corregir el error, reordene los modificadores. Para obtener más información, consulta [Clases y métodos parciales](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).  
  
 El ejemplo siguiente genera la advertencia CS0267:  
  
```  
// CS0267.cs public partial class MyClass { public MyClass() { } } partial public class MyClass  // CS0267 // Try this line instead: // public partial class MyClass { public void Foo() { } public static void Main() { } }  
```