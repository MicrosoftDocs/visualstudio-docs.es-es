---
title: "CA1702: En las palabras compuestas se deber&#237;an utilizar las may&#250;sculas y min&#250;sculas correctamente | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1702"
  - "CompoundWordsShouldBeCasedCorrectly"
helpviewer_keywords: 
  - "CA1702"
  - "CompoundWordsShouldBeCasedCorrectly"
ms.assetid: 05481245-7ad8-48c3-a456-3aa44b6160a6
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1702: En las palabras compuestas se deber&#237;an utilizar las may&#250;sculas y min&#250;sculas correctamente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CompoundWordsShouldBeCasedCorrectly|  
|Identificador de comprobación|CA1702|  
|Categoría|Microsoft.Naming|  
|Cambio problemático|Problemático: cuando se desencadena en ensamblados.<br /><br /> No problemático: cuando se desencadena en parámetros de tipo.|  
  
## Motivo  
 El nombre de un identificador contiene varias palabras y al menos una de ellas parece ser una palabra compuesta en la que no se utilizan correctamente las mayúsculas y minúsculas.  
  
## Descripción de la regla  
 El nombre del identificador se divide en palabras que se basan en el uso de mayúsculas y minúsculas.  La biblioteca de correctores ortográficos de Microsoft comprueba cada combinación de dos palabras contiguas.  Si la reconoce, el identificador genera una infracción de la regla.  Ejemplos de palabras compuestas que originan una infracción son "CheckSum" y "MultiPart", que deberían escribirse como "Checksum" y "Multipart", respectivamente.  Debido a un uso común anterior, hay excepciones que tienen cabida en la regla, y se marcan algunas palabras únicas, como "Toolbar" y "Filename", en las que se deberían utilizar las mayúsculas y minúsculas como si se tratase de dos palabras distintas \(en este caso, "ToolBar" y "FileName"\).  
  
 Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime.  Esto reduce la curva de aprendizaje necesaria para las nuevas bibliotecas de software y aumenta la confianza del cliente respecto a que la biblioteca se haya desarrollado por parte de un especialista en desarrollo de código administrado.  
  
## Cómo corregir infracciones  
 Cambie el nombre utilizando las mayúsculas correctamente.  
  
## Cuándo suprimir advertencias  
 Puede suprimir de forma segura una advertencia de esta regla si el diccionario ortográfico reconoce ambas partes de la palabra compuesta y se pretende utilizar dos palabras.  
  
## Reglas relacionadas  
 [CA1701: En las palabras compuestas de la cadena de recursos se deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
 [CA1709: Los identificadores deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: Los identificadores se deberían diferenciar en algo más que en el uso de mayúsculas y minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
## Vea también  
 [Instrucciones de nomenclatura](../Topic/Naming%20Guidelines.md)   
 [Convenciones de mayúsculas y minúsculas](../Topic/Capitalization%20Conventions.md)