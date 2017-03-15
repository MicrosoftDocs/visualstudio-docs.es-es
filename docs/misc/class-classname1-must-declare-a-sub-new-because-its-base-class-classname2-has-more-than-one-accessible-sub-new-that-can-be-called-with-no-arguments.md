---
title: "La clase &#39;&lt;nombreClase1&gt;&#39; debe declarar un constructor &#39;Sub New&#39; porque su clase base &#39;&lt;nombreClase2&gt;&#39; tiene varios constructores &#39;Sub New&#39; accesibles a los que se puede llamar sin argumentos | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32036"
  - "vbc32036"
helpviewer_keywords: 
  - "BC32036"
ms.assetid: 9b96387e-337e-4b2a-b49f-783c7e13811a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La clase &#39;&lt;nombreClase1&gt;&#39; debe declarar un constructor &#39;Sub New&#39; porque su clase base &#39;&lt;nombreClase2&gt;&#39; tiene varios constructores &#39;Sub New&#39; accesibles a los que se puede llamar sin argumentos
Una clase derivada no declara un constructor y [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] no puede generar uno porque no puede determinar a qué constructor de clase base debe llamar.  
  
 Cuando una clase derivada no declara un constructor, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] intenta generar un constructor implícito sin parámetros que llama a `MyBase.New()`. Si no hay ningún constructor accesible en la clase base al que se pueda llamar sin argumentos, o si hay más de uno, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] no puede generar un constructor implícito.  
  
 Esta situación puede ocurrir, por ejemplo, si un constructor de clase base tiene un argumento `Optional` único y otro tiene un argumento `ParamArray` único. Ambos se pueden llamar sin argumentos.  
  
 **Identificador de error:** BC32036  
  
### Para corregir este error  
  
1.  Declare e implemente al menos un constructor `Sub New` en algún lugar de la clase derivada.  
  
2.  Agregue una llamada a un constructor de clase base, `MyBase.New()`, como la primera línea de cada `Sub New`.  
  
## Vea también  
 [Duración de los objetos: cómo se crean y destruyen](../Topic/Object%20Lifetime:%20How%20Objects%20Are%20Created%20and%20Destroyed%20\(Visual%20Basic\).md)   
 [NO ESTÁ EN LA COMPILACIÓN: Usar constructores y destructores](http://msdn.microsoft.com/es-es/548eebe1-86c4-4377-b2f5-447cb8be3d90)   
 [Optional](/dotnet/visual-basic/language-reference/modifiers/optional)   
 [ParamArray](/dotnet/visual-basic/language-reference/modifiers/paramarray)   
 [Parámetros opcionales](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters)   
 [Matrices de parámetros](/dotnet/visual-basic/programming-guide/language-features/procedures/parameter-arrays)