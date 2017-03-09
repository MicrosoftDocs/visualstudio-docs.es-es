---
title: "Error del compilador CS0759 | Microsoft Docs"
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
  - "CS0759"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0759"
ms.assetid: 96f0e178-adbf-4327-8934-ac282c428184
caps.latest.revision: 4
caps.handback.revision: 4
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0759
No se encuentra ninguna declaración de definición para la declaración de implementación del método parcial 'método'.  
  
 Un método parcial debe tener una declaración de definición que defina la signatura \(nombre, tipo de valor devuelto y parámetros\) del método. El cuerpo de la implementación o el método es opcional.  
  
### Para corregir este error  
  
1.  Proporcione una declaración de definición para el método parcial en la otra parte de una clase o una estructura parciales.  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS0759:  
  
```  
// cs0759.cs using System; public partial class C { partial void Part() // CS0759 { } public static int Main() { return 1; } }  
```  
  
## Vea también  
 [Clases y métodos parciales](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)