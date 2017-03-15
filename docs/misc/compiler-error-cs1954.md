---
title: "Error del compilador CS1954 | Microsoft Docs"
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
  - "CS1954"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1954"
ms.assetid: bdec399e-c43d-46d3-a01b-ef3572786fe5
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1954
El mejor 'método' de correspondencia del método sobrecargado para el elemento inicializador de la colección no se puede usar. Los métodos 'Add' del inicializador de la colección no pueden tener parámetros ref o out.  
  
 Para que una clase de colección se inicialice mediante un inicializador de la colección, la clase debe tener un método `public` `Add` método que no sea un parámetro `ref` ni `out`.  
  
### Para corregir este error  
  
-   Si puede modificar el código fuente de la clase de colección, proporcione un método `Add` que no tome un parámetro `ref` ni `out`.  
  
-   Si no puede modificar la clase de colección, inicialícela con los constructores que proporciona. No puede usar un inicializador de colección con esta.  
  
## Ejemplo  
 En el ejemplo siguiente se genera el error CS1954 porque la única sobrecarga disponible de la lista `Add` en `MyList` tiene un parámetro `ref`.  
  
```  
// cs1954.cs using System.Collections.Generic; class MyList<T> : IEnumerable<T> { List<T> _list; public void Add(ref T item) { _list.Add(item); } public System.Collections.Generic.IEnumerator<T> GetEnumerator() { int index = 0; T current = _list[index]; while (current != null) { yield return _list[index++]; } } System.Collections.IEnumerator System.Collections.IEnumerable.GetEnumerator() { return GetEnumerator(); } } public class MyClass { public string tree { get; set; } } class Program { static void Main(string[] args) { MyList<MyClass> myList = new MyList<MyClass> { new MyClass { tree = "maple" } }; // CS1954 } }  
  
```  
  
## Vea también  
 [Inicializadores de objeto y colección](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers)