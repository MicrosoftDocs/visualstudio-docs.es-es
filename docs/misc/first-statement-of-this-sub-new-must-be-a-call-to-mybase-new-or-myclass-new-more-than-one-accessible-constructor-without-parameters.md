---
title: "La primera instrucci&#243;n de este &#39;Sub New&#39; debe ser una llamada a &#39;MyBase.New&#39; o &#39;MyClass.New&#39; (varios constructores accesibles sin par&#225;metros). | Microsoft Docs"
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
  - "vbc32038"
  - "bc32038"
helpviewer_keywords: 
  - "BC32038"
ms.assetid: 52e4e9df-a85b-46ae-a0cc-7d8fa377fe95
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La primera instrucci&#243;n de este &#39;Sub New&#39; debe ser una llamada a &#39;MyBase.New&#39; o &#39;MyClass.New&#39; (varios constructores accesibles sin par&#225;metros).
La primera instrucción de este 'Sub New' debe ser una llamada a 'MyBase.New' o 'MyClass.New' porque la clase base '\<base\>' de '\<derivada\>' tiene más de un 'Sub New' accesible al que se puede llamar sin argumentos.  
  
 Un constructor de clase no suministra una llamada a un constructor de clase base, y [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] no puede proporcionar una llamada implícita porque no puede determinar qué constructor de clase base debe llamar.  
  
 **Identificador de error:** BC32038  
  
### Para corregir este error  
  
-   Agregue una llamada a un constructor de clase base `MyBase.New()`, o a otro constructor de esta clase usando `MyClass.New()` o `Me.New()`, como la primera línea de este constructor.  
  
## Vea también  
 [Duración de los objetos: cómo se crean y destruyen](../Topic/Object%20Lifetime:%20How%20Objects%20Are%20Created%20and%20Destroyed%20\(Visual%20Basic\).md)   
 [NO ESTÁ EN LA COMPILACIÓN: Usar constructores y destructores](http://msdn.microsoft.com/es-es/548eebe1-86c4-4377-b2f5-447cb8be3d90)   
 [MyBase: eliminar](http://msdn.microsoft.com/es-es/52491d06-6451-4f6f-9aa6-8fab59bbc2b9)