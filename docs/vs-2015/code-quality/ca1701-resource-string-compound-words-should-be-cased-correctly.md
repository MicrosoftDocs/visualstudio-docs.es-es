---
title: 'CA1701: Las palabras compuestas de cadena de recurso deben usarse correctamente | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ResourceStringCompoundWordsShouldBeCasedCorrectly
- CA1701
helpviewer_keywords:
- CA1701
- ResourceStringCompoundWordsShouldBeCasedCorrectly
ms.assetid: 4ddbe09f-24b8-4c47-9373-a06f4487ca0d
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7610852f6d9fbea2fbd2dd10d478ad2d1a0da899
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669269"
---
# <a name="ca1701-resource-string-compound-words-should-be-cased-correctly"></a>CA1701: En las palabras compuestas de la cadena de recursos se deben utilizar mayúsculas y minúsculas correctamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ResourceStringCompoundWordsShouldBeCasedCorrectly|
|Identificador de comprobación|CA1701|
|Categoría|Microsoft.Naming|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Una cadena de recursos contiene una palabra compuesta que no parece ser correcta.

## <a name="rule-description"></a>Descripción de la regla
 Cada palabra de la cadena de recursos se divide en tokens que se basan en el uso de mayúsculas y minúsculas. La biblioteca de correctores ortográficos de Microsoft comprueba cada combinación de dos tokens contiguos. Si la reconoce, la palabra genera una infracción de la regla. Ejemplos de palabras compuestas que causan una infracción son "CheckSum" y "multipart", que deben usarse como "checksum" y "multipart", respectivamente. Debido al uso común anterior, hay varias excepciones integradas en la regla y se marcan varias palabras individuales, como "Toolbar" y "filename", que deben usarse como dos palabras distintas. En este ejemplo, se marcaría "ToolBar" y "FileName".

 Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime. Esto reduce la curva de aprendizaje necesaria para las nuevas bibliotecas de software y aumenta la confianza del cliente respecto a que la biblioteca se haya desarrollado por parte de un especialista en desarrollo de código administrado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Cambie la palabra para que sea correcta.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si el diccionario ortográfico reconoce ambas partes de la palabra compuesta y el objetivo es usar dos palabras.

 También puede agregar palabras compuestas a un diccionario personalizado para el corrector ortográfico. Las palabras del diccionario personalizado no causan infracciones. Para obtener más información, vea [Cómo: Personalizar el Diccionario de análisis de código ](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="related-rules"></a>Reglas relacionadas
 [CA1702: Las palabras compuestas deben tener mayúsculas ](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

 [CA1709: Los identificadores deben tener mayúsculas ](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Los identificadores deben ser diferentes en lugar de Case ](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>Vea también
 [Convenciones de uso de mayúsculas](https://msdn.microsoft.com/library/4c4ea526-9203-486f-b72d-29d61c5b3c6d) [Convenciones de nomenclatura](https://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3)
