---
title: "Error del compilador CS0208 | Microsoft Docs"
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
  - "CS0208"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0208"
ms.assetid: 03534893-1522-4dab-9822-8b9ed97b3bd0
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0208
No se puede adquirir la dirección, obtener el tamaño ni declarar un puntero a un tipo administrado \('type'\)  
  
 Incluso aunque se use con la palabra clave [unsafe](/dotnet/csharp/language-reference/keywords/unsafe), no se permite tomar la dirección de un objeto administrado, obtener su tamaño ni declarar un puntero a un tipo administrado. Un tipo administrado es:  
  
-   cualquier tipo de referencia  
  
-   cualquier estructura que contiene un tipo de referencia como un campo o una propiedad  
  
 Para más información, vea [Código no seguro y punteros](/dotnet/csharp/programming-guide/unsafe-code-pointers/index) y [sizeof](/dotnet/csharp/language-reference/keywords/sizeof).  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0208:  
  
```  
// CS0208.cs // compile with: /unsafe class myClass { public int a = 98; } struct myProblemStruct { string s; float f; } struct myGoodStruct { int i; float f; } public class MyClass { unsafe public static void Main() { // myClass is a class, a managed type. myClass s = new myClass(); myClass* s2 = &s;    // CS0208 // The struct contains a string, a managed type. int i = sizeof(myProblemStruct); //CS0208 // The struct contains only value types. i = sizeof(myGoodStruct); //OK } }  
  
```  
  
## Vea también  
 [sizeof](/dotnet/csharp/language-reference/keywords/sizeof)