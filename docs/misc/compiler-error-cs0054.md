---
title: "Error del compilador CS0054 | Microsoft Docs"
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
  - "CS0054"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0054"
ms.assetid: 49346f55-d887-497a-af71-be4cbbf1de24
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0054
Incoherencia de accesibilidad: el tipo de valor devuelto de indexador 'type' es menos accesible que el indexador 'indexer'  
  
 Una construcción pública debe devolver un objeto accesible públicamente. Para obtener más información, consulta [Modificadores de acceso](/dotnet/csharp/programming-guide/classes-and-structs/access-modifiers).  
  
 El ejemplo siguiente genera la advertencia CS0054:  
  
```  
// CS0054.cs class MyClass // try the following line instead // public class MyClass { } public class MyClass3 { public MyClass this[int i]   // CS0054 { get { return new MyClass(); } } } public class MyClass2 { public static void Main() { } }  
```