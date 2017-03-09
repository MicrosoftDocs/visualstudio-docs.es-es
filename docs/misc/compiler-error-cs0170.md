---
title: "Error del compilador CS0170 | Microsoft Docs"
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
  - "CS0170"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0170"
ms.assetid: ba881e38-2abf-4a5f-b9e6-28d26a5bd235
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0170
Uso del campo 'field' posiblemente sin asignar  
  
 Se usó un campo de una estructura sin inicializarlo primero. Para solucionar este problema, determine primero de qué campo se canceló la inicialización e inicialícelo antes de intentar acceder a este. Para más información acerca de cómo inicializar estructuras, vea [Structs](/dotnet/csharp/programming-guide/classes-and-structs/structs) y [Utilizar estructuras](/dotnet/csharp/programming-guide/classes-and-structs/using-structs).  
  
 El ejemplo siguiente genera la advertencia CS0170:  
  
```  
// CS0170.cs public struct error { public int i; } public class MyClass { public static void Main() { error e; // uncomment the next line to resolve this error // e.i = 0; System.Console.WriteLine( e.i );   // CS0170 because //e.i was never assigned } }  
```