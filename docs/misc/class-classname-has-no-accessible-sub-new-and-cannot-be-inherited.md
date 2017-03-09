---
title: "La clase &#39;&lt;classname&gt;&#39; no tiene un elemento &#39;Sub New&#39; accesible y no se puede heredar | Microsoft Docs"
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
  - "vbc31399"
  - "BC31399"
helpviewer_keywords: 
  - "BC31399"
ms.assetid: 035b333f-ff6a-4fc4-bd36-82f40b1d8bab
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La clase &#39;&lt;classname&gt;&#39; no tiene un elemento &#39;Sub New&#39; accesible y no se puede heredar
Una clase utiliza un elemento [Inherits \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/inherits-statement) para especificar una clase base, pero no puede acceder a ningún constructor de la clase base deseada.  
  
 Esto puede ocurrir si la clase base deseada no tiene constructores o si tiene constructores con niveles de acceso que impiden el acceso desde otra clase.  
  
 Cuando se hereda de una clase, su constructor debería llamar el constructor de clase base mediante [MyBase \- delete](http://msdn.microsoft.com/es-es/52491d06-6451-4f6f-9aa6-8fab59bbc2b9). Si no realiza esta llamada o ni siquiera escribe un constructor explícito, Visual Basic genera un constructor implícito que llama a `MyBase.New()`.  
  
 **Id. de error:** BC31399  
  
### Para corregir este error  
  
1.  Si tiene control de código fuente sobre la clase base deseada, cambie el nivel de acceso de al menos uno de sus constructores para que otra clase pueda acceder a ellos.  
  
2.  Si no puede cambiar los niveles de acceso de los constructores de la clase base deseada, herede de una clase diferente o no herede absolutamente nada.  
  
## Vea también  
 [Inherits \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/inherits-statement)   
 [Fundamentos de la herencia](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)   
 [MyBase \- delete](http://msdn.microsoft.com/es-es/52491d06-6451-4f6f-9aa6-8fab59bbc2b9)   
 [New \(Operador\)](/dotnet/visual-basic/language-reference/operators/new-operator)   
 [Niveles de acceso en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/access-levels)