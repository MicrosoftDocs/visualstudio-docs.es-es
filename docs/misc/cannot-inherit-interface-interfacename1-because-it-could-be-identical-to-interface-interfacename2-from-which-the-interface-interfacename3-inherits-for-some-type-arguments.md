---
title: "No se puede heredar la interfaz &#39;&lt;nombreInterfaz1&gt;&#39; porque podr&#237;a ser id&#233;ntica a la interfaz &#39;&lt;nombreInterfaz2&gt;&#39; de la que se hereda la interfaz &#39;&lt;nombreInterfaz3&gt;&#39; para algunos argumentos de tipo | Microsoft Docs"
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
  - "bc32123"
  - "vbc32123"
helpviewer_keywords: 
  - "BC32123"
ms.assetid: 2b8fa1f0-3d43-45c6-99d0-328151479b43
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se puede heredar la interfaz &#39;&lt;nombreInterfaz1&gt;&#39; porque podr&#237;a ser id&#233;ntica a la interfaz &#39;&lt;nombreInterfaz2&gt;&#39; de la que se hereda la interfaz &#39;&lt;nombreInterfaz3&gt;&#39; para algunos argumentos de tipo
Una interfaz genérica hereda de dos o más interfaces genéricas, y dos de las herencias podrían entrar en conflicto para ciertos valores de argumentos de tipo.  
  
 Las instrucciones siguientes pueden generar este error.  
  
```  
Public Interface interfaceA(Of u) End Interface Public Interface interfaceX(Of v) Inherits interfaceA(Of v) End Interface Public Interface derivedInterface(Of t1, t2) Inherits interfaceA(Of t1), interfaceX(Of t2) End Interface  
```  
  
 Si `derivedInterface` se construye o se implementa al proporcionar el mismo tipo tanto a `t1` como a `t2`, debe heredar dos versiones de `interfaceA` con argumentos de tipo idénticos. Esto produciría ambigüedad sobre a qué versión se debe acceder.  
  
 **Identificador de error:** BC32123  
  
### Para corregir este error  
  
-   Cambie uno de los argumentos de tipo proporcionados a la interfaz derivada para que no haya ningún conflicto.  
  
     O bien  
  
-   Quite de la instrucción `Inherits` una de las interfaces que producen el posible conflicto de herencia o de implementación.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Información general sobre interfaces](http://msdn.microsoft.com/es-es/f96bb470-c1b8-4c73-89bc-6f536b798da1)   
 [Interface \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/interface-statement)   
 [Fundamentos de la herencia](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)   
 [Inherits \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/inherits-statement)   
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)