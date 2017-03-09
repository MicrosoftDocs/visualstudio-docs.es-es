---
title: "Error del compilador CS1520 | Microsoft Docs"
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
  - "CS1520"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1520"
ms.assetid: 1aeeee83-52a6-45dc-b197-a9a6de3a220c
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1520
El método debe tener un tipo de valor devuelto  
  
 Un método declarado en una clase, estructura o interfaz debe tener un tipo de valor devuelto explícito. En el ejemplo siguiente, el método Square tiene un valor devuelto de [cadena](/dotnet/csharp/language-reference/keywords/string):  
  
```  
class Test { string IntToString(int i) { return i.ToString(); } }  
```  
  
 El ejemplo siguiente genera la advertencia CS1520:  
  
```  
// CS1520a.cs public class x { // Method declaration missing a return type MyMethod()   // CS1520 {} // Add the desired return type: // void MyMethod2() // { } public static void Main() { } }  
```  
  
 Este error también puede producirse si el caso de nombre de un constructor difiere del de la declaración de clase o estructura, como en el ejemplo siguiente. Dado que el nombre no es exactamente el mismo que el nombre de clase, el compilador lo interpreta como un método normal, no como un constructor, y genera el error:  
  
```  
// CS1520b.cs public class Class1 { // Should be Class1, not class1 public class1()   // CS1520 { } static void Main() { } }  
```  
  
## Vea también  
 [Métodos](/dotnet/csharp/programming-guide/classes-and-structs/methods)   
 [Constructores](/dotnet/csharp/programming-guide/classes-and-structs/constructors)