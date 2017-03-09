---
title: "No se puede heredar la interfaz &#39;&lt;nombreInterfaz1&gt;&#39; porque la interfaz &#39;&lt;nombreInterfaz2&gt;&#39; de la que se hereda podr&#237;a ser id&#233;ntica a la interfaz &#39;&lt;nombreInterfaz3&gt;&#39; para algunos argumentos de tipo. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32121"
  - "vbc32121"
helpviewer_keywords: 
  - "BC32121"
ms.assetid: 56b1167e-f626-4a27-8395-9d396cc209f2
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se puede heredar la interfaz &#39;&lt;nombreInterfaz1&gt;&#39; porque la interfaz &#39;&lt;nombreInterfaz2&gt;&#39; de la que se hereda podr&#237;a ser id&#233;ntica a la interfaz &#39;&lt;nombreInterfaz3&gt;&#39; para algunos argumentos de tipo.
Una interfaz genérica hereda de dos o más interfaces genéricas, y ciertos valores de argumentos de tipo de dos de las herencias podrían entran en conflicto.  
  
 Las instrucciones siguientes pueden generar este error.  
  
```  
Public Interface interfaceA(Of u) Inherits interfaceX(Of u) End Interface Public Interface interfaceX(Of v) End Interface Public Interface derivedInterface(Of t1, t2) Inherits interfaceA(Of t1), interfaceX(Of t2) End Interface  
```  
  
 Si `derivedInterface` se construye o implementa suministrando el mismo tipo para `t1` y `t2`, debe heredar dos versiones de `interfaceX` con argumentos de tipo idénticos. Esto produciría ambigüedad sobre a qué versión se debe acceder.  
  
 **Identificador de error:** BC32121  
  
### Para corregir este error  
  
-   Cambie uno de los argumentos de tipo proporcionados a la interfaz derivada para que no haya ningún conflicto.  
  
     O bien  
  
-   Quite de la instrucción `Inherits` una de las interfaces que producen el posible conflicto de herencia o de implementación.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Información general de las interfaces](http://msdn.microsoft.com/es-es/f96bb470-c1b8-4c73-89bc-6f536b798da1)   
 [Interface \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/interface-statement)   
 [Fundamentos de la herencia](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)   
 [Inherits \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/inherits-statement)   
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)