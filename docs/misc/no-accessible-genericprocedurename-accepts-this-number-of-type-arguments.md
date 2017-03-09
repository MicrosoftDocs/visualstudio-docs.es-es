---
title: "Ninguna de las funciones &#39;&lt;nombreDeProcedimientoGen&#233;rico&gt;&#39; accesibles acepta este n&#250;mero de argumentos de tipo | Microsoft Docs"
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
  - "bc32118"
  - "vbc32118"
helpviewer_keywords: 
  - "BC32118"
ms.assetid: 4ee942ba-0fa1-4ec1-9c2c-a0c0dc3f1b17
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ninguna de las funciones &#39;&lt;nombreDeProcedimientoGen&#233;rico&gt;&#39; accesibles acepta este n&#250;mero de argumentos de tipo
Una instrucción llama a un procedimiento genérico que tiene más de una versión sobrecargada, pero ninguna de las versiones sobrecargadas define el mismo número de parámetros de tipo como el número de argumentos de tipo proporcionados en la llamada.  
  
 Si solo existe una versión genérica, se llama sin argumentos de tipo y el compilador puede intentar realizar la *inferencia de tipos*. Para más información, vea "Inferencia de tipos" en [Procedimientos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures). Sin embargo, si hay más de una versión genérica, el compilador no será capaz de elegir entre ellas a menos que proporcione los argumentos de tipo. Si proporciona un argumento de tipo, debe proporcionar un argumento de tipo para cada parámetro de tipo definido por una de las versiones sobrecargadas.  
  
 **Identificador de error:** BC32118  
  
### Para corregir este error  
  
-   Decida qué versión sobrecargada desea llamar y, después, proporcione el número adecuado de argumentos de tipo.  
  
## Vea también  
 [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)   
 [Sobrecarga de procedimientos](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading)   
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Procedimientos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)