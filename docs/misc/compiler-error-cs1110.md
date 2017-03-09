---
title: "Error del compilador CS1110 | Microsoft Docs"
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
  - "CS1110"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1110"
ms.assetid: 5b571a76-1891-4f33-b23d-7c4cc654a05f
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1110
No puede usar el modificador 'this' en el primer parámetro de la declaración de método sin una referencia a System.Core.dll. Agregue una referencia a System.Core.dll o quite el modificador 'this' de la declaración del método.  
  
 Los métodos de extensión se admiten en la versión 3.5 y versiones posterior de .NET Framework. Estos métodos generan metadatos que marcan el método con un atributo. La clase de atributo está en system.core.dll.  
  
### Para corregir este error  
  
1.  Como se indica en el mensaje, agregue una referencia a System.Core.dll o quite el modificador `this` de la declaración del método.  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS1110 si el archivo no se compila con una referencia a System.Core.dll:  
  
```  
// cs1110.cs // CS1110 // Compile with: /target:library public static class Extensions { public static bool Test(this bool b) { return b; } }  
```  
  
## Vea también  
 [Métodos de extensión](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)