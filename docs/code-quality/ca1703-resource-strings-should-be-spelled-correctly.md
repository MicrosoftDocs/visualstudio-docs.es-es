---
title: "CA1703: Las cadenas de recursos deber&#237;an tener la ortograf&#237;a correcta | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ResourceStringsShouldBeSpelledCorrectly"
  - "CA1703"
helpviewer_keywords: 
  - "CA1703"
  - "ResourceStringsShouldBeSpelledCorrectly"
ms.assetid: 693f4970-f512-40cb-ae3b-a0f3a5c6d6f1
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA1703: Las cadenas de recursos deber&#237;an tener la ortograf&#237;a correcta
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ResourceStringsShouldBeSpelledCorrectly|  
|Identificador de comprobación|CA1703|  
|Categoría|Microsoft.Naming|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Una cadena de recurso contiene una o varias palabras que la biblioteca de correctores ortográficos de Microsoft no reconoce.  
  
## Descripción de la regla  
 Esta regla analiza la cadena de recurso en palabras \(convirtiendo las palabras compuestas en tokens\) y comprueba la ortografía de cada palabra o token.  Para obtener información sobre el algoritmo de análisis, vea [CA1704: Los identificadores deberían tener la ortografía correcta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
 De forma predeterminada, se utiliza la versión inglesa \(en\) del corrector ortográfico.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, utilice palabras completas que estén escritas correctamente o agregue las palabras a un diccionario personalizado.  Para obtener información sobre cómo utilizar diccionarios personalizados, vea [CA1704: Los identificadores deberían tener la ortografía correcta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  Las palabras escritas correctamente reducen el tiempo de aprendizaje necesario para las nuevas bibliotecas de software.  
  
## Reglas relacionadas  
 [CA1701: En las palabras compuestas de la cadena de recursos se deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
 [CA1704: Los identificadores deberían tener la ortografía correcta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
 [CA2204: Debe escribir correctamente los literales](../code-quality/ca2204-literals-should-be-spelled-correctly.md)