---
title: "Error del compilador CS0755 | Microsoft Docs"
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
  - "CS0755"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0755"
ms.assetid: 80613029-a009-4bdf-b1c2-1eec1e60c7b4
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0755
Ambas declaraciones de método parcial deben ser métodos de extensión; de lo contrario, no puede serlo ninguna de las dos.  
  
 Un método parcial consta de una declaración de definición \(firma\) y una declaración de implementación opcional \(cuerpo\). Si la declaración de definición es un método de extensión, la declaración de implementación, si se define una, también debe ser un método de extensión. Asimismo, si el método de definición no es un método de extensión, la implementación tampoco debe serlo.  
  
### Para corregir este error  
  
1.  Quite le modificador `this` de una de las partes, o agréguelo a la otra.  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS0755:  
  
```  
// cs0755.cs public static partial class Ext { static partial void Part(this C c); //Extension method // Typically the implementing declaration is in a separate file. static partial void Part(C c) //CS0755 { } } public partial class C { public static int Main() { return 1; } }  
```  
  
## Vea también  
 [Métodos de extensión](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)