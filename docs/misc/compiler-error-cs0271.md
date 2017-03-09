---
title: "Error del compilador CS0271 | Microsoft Docs"
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
  - "CS0271"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0271"
ms.assetid: eadc9fb5-7770-4ec4-94f6-3c7cf37eec06
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0271
La propiedad o el indexador 'property\/indexer' no se pueden usar en este contexto porque el descriptor de acceso get es inaccesible  
  
 Este error se produce cuando se intenta acceder a un descriptor de acceso `get` inaccesible. Para resolver este error, aumente la accesibilidad del descriptor de acceso o cambie la ubicación de la llamada. Para más información, vea [Accesibilidad del descriptor de acceso](/dotnet/csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility) y [Propiedades](/dotnet/csharp/programming-guide/classes-and-structs/properties).  
  
 El ejemplo siguiente genera el error CS0271:  
  
```  
// CS0271.cs public class MyClass { public int Property { private get { return 0; } set { } } public int Property2 { get { return 0; } set { } } } public class Test { public static void Main(string[] args) { MyClass c = new MyClass(); int a = c.Property;   // CS0271 int b = c.Property2;   // OK } }  
```