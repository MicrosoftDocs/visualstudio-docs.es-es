---
title: "Error del compilador CS1654 | Microsoft Docs"
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
  - "CS1654"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1654"
ms.assetid: 471c1298-1908-449d-b765-8dc3cd81a11d
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1654
No puede modificar miembros de 'variable' porque es un 'tipo de variable de solo lectura'.  
  
 Este error se produce cuando se intentan modificar miembros de una variable que es de solo lectura porque está en una construcción especial.  
  
 Un área habitual en que ocurre esto es dentro de bucles [foreach](/dotnet/csharp/language-reference/keywords/foreach-in). Es un error en tiempo de compilación modificar el valor de los elementos de la colección. Por lo tanto, no puede realizar modificaciones en los elementos que son [tipos de valor](/dotnet/csharp/language-reference/keywords/value-types), incluidas las [structs](/dotnet/csharp/programming-guide/classes-and-structs/structs). En una colección cuyos elementos son [tipos de referencia](/dotnet/csharp/language-reference/keywords/reference-types), puede modificar los miembros accesibles de cada elemento, pero cualquier intento de agregar, eliminar o reemplazar elementos completos generará el [Compiler Error CS1656](/dotnet/csharp/language-reference/compiler-messages/cs1656).  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS1654 porque `Book` es una `struct`. Para corregir el error, cambie la `struct` a una [class](/dotnet/csharp/language-reference/keywords/class).  
  
```  
using System.Collections.Generic; using System.Text; namespace CS1654 { struct Book { public string Title; public string Author; public double Price; public Book(string t, string a, double p) { Title=t; Author=a; Price=p; } } class Program { List<Book> list; static void Main(string[] args) { //Use a collection initializer to initialize the list Program prog = new Program(); prog.list = new List<Book>(); prog.list.Add(new Book ("The C# Programming Language", "Hejlsberg, Wiltamuth, Golde", 29.95)); prog.list.Add(new Book ("The C++ Programming Language", "Stroustrup", 29.95)); prog.list.Add(new Book ("The C Programming Language", "Kernighan, Ritchie", 29.95)); foreach(Book b in prog.list) { //Compile error if Book is a struct //Make Book a class to modify its members b.Price +=9.95; // CS1654 } } } }  
  
```