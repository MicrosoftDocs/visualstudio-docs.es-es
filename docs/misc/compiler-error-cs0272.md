---
title: "Error del compilador CS0272 | Microsoft Docs"
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
  - "CS0272"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0272"
ms.assetid: 16a9aab6-922a-45a3-a0ef-f32e99f3950f
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0272
La propiedad o el indexador 'property\/indexer' no se puede usar en este contexto porque el descriptor de acceso set es inaccesible  
  
 Este error se produce cuando el descriptor de acceso `set` no es accesible para el código de programa. Para resolver este error, aumente la accesibilidad del descriptor de acceso o cambie la ubicación de la llamada. Para obtener más información, consulta [Restringir la accesibilidad del descriptor de acceso](/dotnet/csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility).  
  
## Ejemplo  
 El siguiente ejemplo genera el error CS0272:  
  
```  
// CS0272.cs public class MyClass { public int Property { get { return 0; } private set { } } } public class Test { static void Main() { MyClass c = new MyClass(); c.Property = 10;      // CS0272 // To resolve, remove the previous line // or use an appropriate modifier on the set accessor. } }  
```