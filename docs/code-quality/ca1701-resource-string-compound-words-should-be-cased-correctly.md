---
title: "CA1701: Palabras compuestas de la cadena de recurso deben ser mayúsculas y minúsculas correctamente | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ResourceStringCompoundWordsShouldBeCasedCorrectly
- CA1701
helpviewer_keywords:
- CA1701
- ResourceStringCompoundWordsShouldBeCasedCorrectly
ms.assetid: 4ddbe09f-24b8-4c47-9373-a06f4487ca0d
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0b4b154d6e959e636ee75481816a2424d5ea2e18
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="ca1701-resource-string-compound-words-should-be-cased-correctly"></a>CA1701: En las palabras compuestas de la cadena de recursos se deberían utilizar las mayúsculas y minúsculas correctamente
|||  
|-|-|  
|TypeName|ResourceStringCompoundWordsShouldBeCasedCorrectly|  
|Identificador de comprobación|CA1701|  
|Categoría|Microsoft.Naming|  
|Cambio problemático|Poco problemático|  
  
## <a name="cause"></a>Motivo  
 Una cadena de recurso contiene una palabra compuesta en la que no aparecen en mayúsculas y minúsculas correctamente.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Cada palabra en la cadena de recursos se divide en tokens que se basan en las mayúsculas y minúsculas. La biblioteca de correctores ortográficos de Microsoft comprueba cada combinación de dos tokens contiguos. Si la reconoce, la palabra genera una infracción de la regla. Ejemplos de palabras compuestas que producen una infracción son "CheckSum" y "MultiPart", que debe escribirse como "Checksum" y "Multipart", respectivamente. Debido a un uso común anterior, se generan varias excepciones en la regla y se marcan algunas palabras únicas, como "Toolbar" y "Filename", que debería escribirse como dos palabras distintas. En este ejemplo, debería marcarse "ToolBar" y "FileName".  
  
 Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime. Esto reduce la curva de aprendizaje necesaria para las nuevas bibliotecas de software y aumenta la confianza del cliente respecto a que la biblioteca se haya desarrollado por parte de un especialista en desarrollo de código administrado.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Cambie la palabra para que lo es mayúsculas y minúsculas correctamente.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla si ambas partes de la palabra compuesta se reconocen por el diccionario de ortografía y la intención es usar dos o más palabras.  
  
 También puede agregar palabras compuestas a un diccionario personalizado para el corrector ortográfico. Las palabras en el diccionario personalizado no producen infracciones. Para obtener más información, consulte [Cómo: personalizar el diccionario de análisis de código](../code-quality/how-to-customize-the-code-analysis-dictionary.md).  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [CA1702: En las palabras compuestas se deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
 [CA1709: Los identificadores deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: Los identificadores se deberían diferenciar en algo más que en el uso de mayúsculas y minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
## <a name="see-also"></a>Vea también  
 [Convenciones de mayúsculas y minúsculas](/dotnet/standard/design-guidelines/capitalization-conventions)   
 [Instrucciones de nomenclatura](/dotnet/standard/design-guidelines/naming-guidelines)