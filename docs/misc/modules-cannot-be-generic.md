---
title: "Los m&#243;dulos no pueden ser gen&#233;ricos. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BC32073"
  - "vbc32073"
helpviewer_keywords: 
  - "BC32073"
ms.assetid: 47246e2b-51d4-4a10-a3ac-bc77b44fa2ca
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los m&#243;dulos no pueden ser gen&#233;ricos.
Una instrucción `Module` usa la palabra clave `Of` para introducir parámetros de tipo genérico.  
  
 Puede definir y usar clases genéricas, estructuras, interfaces, procedimientos y delegados. No puede definir módulos genéricos.  
  
 **Identificador de error:** BC32073  
  
### Para corregir este error  
  
1.  Quite la palabra clave `Of` de la instrucción `Module`.  
  
2.  Si quiere la función de un módulo genérico, la aproximación más similar es una clase genérica. Use una [Class \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/class-statement) en lugar de una instrucción `Module`.  
  
## Vea también  
 [Module \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/module-statement)   
 [Of](/dotnet/visual-basic/language-reference/statements/of-clause)   
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Cómo: Definir una clase que pueda proporcionar la misma funcionalidad en tipos de datos diferentes](../Topic/How%20to:%20Define%20a%20Class%20That%20Can%20Provide%20Identical%20Functionality%20on%20Different%20Data%20Types%20\(Visual%20Basic\).md)