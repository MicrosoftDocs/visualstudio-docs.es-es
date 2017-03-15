---
title: "Advertencia del compilador (nivel 2) CS0435 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0435"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0435"
ms.assetid: e70cd8c1-d399-4af8-8b1e-69a1de389aad
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 2) CS0435
El espacio de nombres 'espacioNombres' de 'ensamblado' está en conflicto con el tipo importado 'tipo' en 'ensamblado'. Uso del espacio de nombres definido en 'ensamblado'.  
  
 Esta advertencia se emite cuando un espacio de nombres de un archivo de origen \(archivo\_2\) está en conflicto con un tipo importado de archivo\_1. El compilador usa el del archivo de origen.  
  
 El ejemplo siguiente genera el error CS0435:  
  
 Compile este archivo primero:  
  
```  
// CS0435_1.cs // compile with: /t:library public class Util { public class A { } }  
```  
  
 A continuación, compile este archivo:  
  
```  
// CS0435_2.cs // compile with: /r:CS0435_1.dll using System; namespace Util { public class A { } } public class Test { public static void Main() { Console.WriteLine(typeof(Util.A)); // CS0435 } }  
```