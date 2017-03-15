---
title: "CA1701: En las palabras compuestas de la cadena de recursos se deber&#237;an utilizar las may&#250;sculas y min&#250;sculas correctamente | Microsoft Docs"
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
  - "ResourceStringCompoundWordsShouldBeCasedCorrectly"
  - "CA1701"
helpviewer_keywords: 
  - "CA1701"
  - "ResourceStringCompoundWordsShouldBeCasedCorrectly"
ms.assetid: 4ddbe09f-24b8-4c47-9373-a06f4487ca0d
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1701: En las palabras compuestas de la cadena de recursos se deber&#237;an utilizar las may&#250;sculas y min&#250;sculas correctamente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ResourceStringCompoundWordsShouldBeCasedCorrectly|  
|Identificador de comprobación|CA1701|  
|Categoría|Microsoft.Naming|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Una cadena de recursos contiene una palabra compuesta en la que parece que no se utilizan correctamente las mayúsculas y minúsculas.  
  
## Descripción de la regla  
 Cada palabra en la cadena de recursos se divide en tokens basándose en el uso de mayúsculas y minúsculas.  La biblioteca de correctores ortográficos de Microsoft comprueba cada combinación de dos tokens contiguos.  Si la reconoce, la palabra genera una infracción de la regla.  Ejemplos de palabras compuestas que originan una infracción son "CheckSum" y "MultiPart", que deberían escribirse como "Checksum" y "Multipart", respectivamente.  Debido a un uso común anterior, hay excepciones que tienen cabida en la regla, y se marcan algunas palabras únicas, como "Toolbar" y "Filename", en las que se deberían utilizar las mayúsculas y minúsculas como si se tratase de dos palabras distintas.  En este ejemplo, debería marcarse "Toolbar" y "FileName".  
  
 Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime.  Esto reduce la curva de aprendizaje necesaria para las nuevas bibliotecas de software y aumenta la confianza del cliente respecto a que la biblioteca se haya desarrollado por parte de un especialista en desarrollo de código administrado.  
  
## Cómo corregir infracciones  
 Cambie la palabra de modo que el uso de mayúsculas y minúsculas sea correcto.  
  
## Cuándo suprimir advertencias  
 Puede suprimir de forma segura una advertencia de esta regla si el diccionario ortográfico reconoce ambas partes de la palabra compuesta y se pretende utilizar dos palabras.  
  
 También puede agregar palabras compuestas a un diccionario personalizado para el corrector ortográfico.  Las palabras del diccionario personalizado no producen infracciones.  Para obtener más información, vea [Cómo: Personalizar el diccionario de análisis de código](../code-quality/how-to-customize-the-code-analysis-dictionary.md).  
  
## Reglas relacionadas  
 [CA1702: En las palabras compuestas se deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
 [CA1709: Los identificadores deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: Los identificadores se deberían diferenciar en algo más que en el uso de mayúsculas y minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
## Vea también  
 [Convenciones de mayúsculas y minúsculas](../Topic/Capitalization%20Conventions.md)   
 [Instrucciones de nomenclatura](../Topic/Naming%20Guidelines.md)