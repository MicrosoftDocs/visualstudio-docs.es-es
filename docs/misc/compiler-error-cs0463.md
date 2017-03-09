---
title: "Error del compilador CS0463 | Microsoft Docs"
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
  - "CS0463"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0463"
ms.assetid: 0cb4be4e-86ea-4ade-8817-b17d4cacd4d5
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0463
No se pudo realizar la evaluación de la expresión de la constante decimal y se produjo un error: 'error'  
  
 Este error se produce cuando una expresión constante decimal se desborda en tiempo de compilación.  
  
 Los errores de desbordamiento suelen producirse en tiempo de ejecución. En este caso, se ha definido la expresión de constante de tal manera que el compilador pudo evaluar el resultado y saber que podría producirse un desbordamiento.  
  
## Ejemplo  
 El código siguiente genera el error CS0463:  
  
```  
// CS0463.cs using System; class MyClass { public static void Main() { const decimal myDec = 79000000000000000000000000000.0m + 79000000000000000000000000000.0m; // CS0463 Console.WriteLine(myDec.ToString()); } }  
```