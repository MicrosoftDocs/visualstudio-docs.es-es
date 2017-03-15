---
title: "Error del compilador CS0119 | Microsoft Docs"
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
  - "CS0119"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0119"
ms.assetid: 048924f1-378f-4021-bd20-299d3218f810
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0119
'construct1\_name' es de tipo 'construct1', que no es válido en el contexto especificado.  
  
 El compilador detectó una construcción inesperada, como la siguiente:  
  
-   Un constructor de clase no es una expresión de prueba válida en una instrucción condicional.  
  
-   Se utilizó un nombre de clase en lugar de un nombre de instancia para hacer referencia a un elemento de matriz.  
  
-   Se utiliza un identificador de método como si fuera una clase o una estructura  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0119.  
  
```  
// CS0119.cs using System; public class MyClass { public static void Test() {} public static void Main() { Console.WriteLine(Test.x);   // CS0119 } }  
```