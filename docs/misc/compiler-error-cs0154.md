---
title: "Error del compilador CS0154 | Microsoft Docs"
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
  - "CS0154"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0154"
ms.assetid: 815150da-09b4-4593-825f-1dd435c92da8
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0154
La propiedad o el indexador 'property' no se puede usar en este contexto porque carece del descriptor de acceso get.  
  
 Error al intentar usar [property](/dotnet/csharp/programming-guide/classes-and-structs/using-properties) porque no se definió ningún método de descriptor de acceso get en la propiedad. Para obtener más información, consulta [Campos](/dotnet/csharp/programming-guide/classes-and-structs/fields).  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0154:  
  
```  
// CS0154.cs public class MyClass2 { public int i { set { } // uncomment the get method to resolve this error /* get { return 0; } */ } } public class MyClass { public static void Main() { MyClass2 myClass2 = new MyClass2(); int j = myClass2.i;   // CS0154, no get method } }  
```