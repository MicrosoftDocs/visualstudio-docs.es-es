---
title: "Error del compilador CS0202 | Microsoft Docs"
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
  - "CS0202"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0202"
ms.assetid: 7088850f-c206-4b95-9586-a0fa3d876c0c
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0202
foreach requiere que el tipo de valor devuelto 'type' de 'type.GetEnumerator\(\)' tenga un método MoveNext público y una propiedad Current pública adecuados  
  
 Una función <xref:System.Collections.IEnumerable.GetEnumerator%2A>, que se usa para habilitar el uso de instrucciones foreach, no puede devolver un puntero o una matriz; debe devolver una instancia de clase que puede actuar como enumerador. Los requisitos apropiados para actuar como enumerador incluyen una propiedad Current pública y un método MoveNext público.  
  
> [!NOTE]
>  En C\# 2.0, el compilador generará automáticamente Current y MoveNext. Para más información y ver un código de ejemplo, vea [Interfaces genéricas](/dotnet/csharp/programming-guide/generics/generic-interfaces).  
  
 El ejemplo siguiente genera la advertencia CS0202:  
  
```  
// CS0202.cs public class C1 { public int Current { get { return 0; } } public bool MoveNext () { return false; } public static implicit operator C1 (int c1) { return 0; } } public class C2 { public int Current { get { return 0; } } public bool MoveNext () { return false; } public C1[] GetEnumerator () // try the following line instead // public C1 GetEnumerator () { return null; } } public class MainClass { public static void Main () { C2 c2 = new C2(); foreach (C1 x in c2)   // CS0202 { System.Console.WriteLine(x.Current); } } }  
```