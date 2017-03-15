---
title: "Las clases gen&#233;ricas o contenidas en un tipo gen&#233;rico no pueden heredar de una clase de atributos | Microsoft Docs"
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
  - "vbc32074"
  - "BC32074"
helpviewer_keywords: 
  - "BC32074"
ms.assetid: 3552ac98-d86a-4962-9d51-b9a8acc38ea1
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Las clases gen&#233;ricas o contenidas en un tipo gen&#233;rico no pueden heredar de una clase de atributos
Una clase genérica o anidada dentro de un tipo genérico especifica que hereda de una clase de atributo.  
  
 Visual Basic y .NET Framework no admiten actualmente ninguna combinación de atributos y tipos genéricos. Esto significa que se aplican las siguientes limitaciones:  
  
-   Un atributo no puede ser un tipo genérico ni declararse dentro de un tipo genérico.  
  
-   Un atributo no puede heredar de una clase genérica, ni una clase genérica puede heredar de un atributo.  
  
-   Cuando se aplica un atributo, no se puede proporcionar un argumento que sea cualquiera de los siguientes:  
  
    -   Un tipo genérico  
  
    -   Un tipo construido a partir de un tipo genérico  
  
    -   Un parámetro de tipo de un tipo de contenedor  
  
    -   Un tipo construido a partir de un parámetro de tipo de un tipo contenedor  
  
 **Id. de error:** BC32074  
  
### Para corregir este error  
  
-   Cambie la clase base a algo distinto de una clase de atributo o quite por completo la instrucción `Inherits`.  
  
## Vea también  
 <xref:System.Attribute>   
 [NO ESTÁ EN LA COMPILACIÓN: Información general de atributos en Visual Basic](http://msdn.microsoft.com/es-es/0d0cff64-892d-4f57-83bd-bef388553d4f)   
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Fundamentos de la herencia](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)   
 [Inherits \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/inherits-statement)