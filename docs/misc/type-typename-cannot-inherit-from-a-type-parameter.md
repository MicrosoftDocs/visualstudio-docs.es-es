---
title: "El tipo &#39;&lt;nombreDeTipo&gt;&#39; no puede heredar de un par&#225;metro de tipo. | Microsoft Docs"
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
  - "bc32055"
  - "vbc32055"
helpviewer_keywords: 
  - "BC32055"
ms.assetid: 97af7cad-6e40-41e3-892d-1fbcbd86356d
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El tipo &#39;&lt;nombreDeTipo&gt;&#39; no puede heredar de un par&#225;metro de tipo.
Una clase o una interfaz incluye una [Inherits \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/inherits-statement) que especifica un parámetro de tipo genérico.  
  
 Un tipo no puede heredar de un tipo que aún no se ha definido. La herencia implica la capacidad de volver a usar los miembros de la clase base, lo que a su vez requiere que estos miembros estén definidos. Un parámetro de tipo genérico es un marcador de posición que se reemplazará por un tipo específico proporcionado por un argumento de tipo. Por lo tanto, un tipo no puede heredar del marcador de posición.  
  
 **Identificador de error:** BC32055  
  
### Para corregir este error  
  
-   Si el tipo que hereda debe heredar de otro tipo, use un tipo específico en lugar de un parámetro de tipo.  
  
-   Si el tipo base debe estar representado por un parámetro de tipo genérico, ningún otro tipo puede heredar de él. Quite [Inherits \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/inherits-statement).  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Herencia en Visual Basic](http://msdn.microsoft.com/es-es/e5e6e240-ed31-4657-820c-079b7c79313c)   
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)