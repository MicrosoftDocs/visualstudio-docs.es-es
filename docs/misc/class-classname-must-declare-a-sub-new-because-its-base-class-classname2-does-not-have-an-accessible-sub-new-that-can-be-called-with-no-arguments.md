---
title: "La clase &#39;&lt;nombreClase&gt;&#39; debe declarar un &#39;Sub New&#39; porque su clase base &#39;&lt;nombreClase&gt;&#39; no dispone de un &#39;Sub New&#39; accesible al que se pueda llamar sin argumentos. | Microsoft Docs"
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
  - "vbc30387"
  - "bc30387"
helpviewer_keywords: 
  - "BC30387"
ms.assetid: ff587e79-fa47-4b55-9a08-24688b209e0a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La clase &#39;&lt;nombreClase&gt;&#39; debe declarar un &#39;Sub New&#39; porque su clase base &#39;&lt;nombreClase&gt;&#39; no dispone de un &#39;Sub New&#39; accesible al que se pueda llamar sin argumentos.
Una clase derivada no declara un constructor y [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] no puede generar uno porque no hay ningún constructor de clase base que se pueda llamar.  
  
 Cuando una clase derivada no declara un constructor, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] intenta generar un constructor sin parámetros implícito que llama a `MyBase.New()`. Si no hay ningún constructor accesible en la clase base que se pueda llamar sin argumentos, o si hay más de uno, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] no puede generar un constructor implícito.  
  
 **Identificador de error:** BC30387  
  
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