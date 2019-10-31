---
title: 'CA1702: Las palabras compuestas deben usarse correctamente | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
helpviewer_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
ms.assetid: 05481245-7ad8-48c3-a456-3aa44b6160a6
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 76ce346430a249b562f00e17c3173e79128d1708
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669253"
---
# <a name="ca1702-compound-words-should-be-cased-correctly"></a>CA1702: En las palabras compuestas se deben utilizar mayúsculas y minúsculas correctamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para obtener la documentación más reciente sobre Visual Studio, vea [CA1702: Las palabras compuestas deben tener mayúsculas ](https://docs.microsoft.com/visualstudio/code-quality/ca1702-compound-words-should-be-cased-correctly) correctamente.

|||
|-|-|
|TypeName|CompoundWordsShouldBeCasedCorrectly|
|Identificador de comprobación|CA1702|
|Categoría|Microsoft.Naming|
|Cambio problemático|Problemático: cuando se desencadena en ensamblados.<br /><br /> No problemático: cuando se desencadena en parámetros de tipo.|

## <a name="cause"></a>Motivo
 El nombre de un identificador contiene varias palabras y al menos una de las palabras parece ser una palabra compuesta que no se ha puesto en mayúsculas correctamente.

## <a name="rule-description"></a>Descripción de la regla
 El nombre del identificador se divide en palabras que se basan en el uso de mayúsculas y minúsculas. La biblioteca del corrector ortográfico de Microsoft comprueba cada combinación de dos palabras contiguas. Si se reconoce, el identificador produce una infracción de la regla. Ejemplos de palabras compuestas que causan una infracción son "CheckSum" y "multipart", que deben usarse como "checksum" y "multipart", respectivamente. Debido al uso común anterior, hay varias excepciones integradas en la regla y se marcan varias palabras individuales, como "Toolbar" y "filename", que deben usarse como dos palabras distintas (en este caso, "ToolBar" y "FileName").

 Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime. Esto reduce la curva de aprendizaje necesaria para las nuevas bibliotecas de software y aumenta la confianza del cliente respecto a que la biblioteca se haya desarrollado por parte de un especialista en desarrollo de código administrado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Cambie el nombre para que sea correcto.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si el diccionario ortográfico reconoce ambas partes de la palabra compuesta y el objetivo es usar dos palabras.

## <a name="related-rules"></a>Reglas relacionadas
 [CA1701: Las palabras compuestas de cadena de recurso deben tener mayúsculas ](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

 [CA1709: Los identificadores deben tener mayúsculas ](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Los identificadores deben ser diferentes en lugar de Case ](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>Vea también
 [Convenciones de nomenclatura](https://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3) [ Convenciones de uso de mayúsculas](https://msdn.microsoft.com/library/4c4ea526-9203-486f-b72d-29d61c5b3c6d)
