---
title: 'CA1701: Palabras compuestas de la cadena de recursos deberían escribirse correctamente | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- ResourceStringCompoundWordsShouldBeCasedCorrectly
- CA1701
helpviewer_keywords:
- CA1701
- ResourceStringCompoundWordsShouldBeCasedCorrectly
ms.assetid: 4ddbe09f-24b8-4c47-9373-a06f4487ca0d
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 525f08cfd69b8ebac30b4b3455b71b0ebb16c90e
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591632"
---
# <a name="ca1701-resource-string-compound-words-should-be-cased-correctly"></a>CA1701: En las palabras compuestas de la cadena de recursos se deberían utilizar las mayúsculas y minúsculas correctamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [CA1701: palabras compuestas de la cadena de recursos deberían escribirse correctamente](https://docs.microsoft.com/visualstudio/code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly).

|||
|-|-|
|TypeName|ResourceStringCompoundWordsShouldBeCasedCorrectly|
|Identificador de comprobación|CA1701|
|Categoría|Microsoft.Naming|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Una cadena de recursos contiene una palabra compuesta que no aparece en mayúsculas y minúsculas correctamente.

## <a name="rule-description"></a>Descripción de la regla
 Cada palabra de la cadena de recursos se divide en tokens que se basan en las mayúsculas y minúsculas. La biblioteca de correctores ortográficos de Microsoft comprueba cada combinación de dos tokens contiguos. Si la reconoce, la palabra genera una infracción de la regla. Ejemplos de palabras compuestas que originan una infracción son "CheckSum" y "MultiPart", que debería escribirse como "Checksum" y "Multipart", respectivamente. Debido al uso común anterior, se generan varias excepciones a la regla, y se marcan algunas palabras únicas, como "Toolbar" y "Filename", que debería escribirse como dos palabras distintas. En este ejemplo, debería marcarse "ToolBar" y "FileName".

 Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime. Esto reduce la curva de aprendizaje necesaria para las nuevas bibliotecas de software y aumenta la confianza del cliente respecto a que la biblioteca se haya desarrollado por parte de un especialista en desarrollo de código administrado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Cambiar la palabra para que utilizando las mayúsculas correctamente.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si el diccionario ortográfico reconoce ambas partes de la palabra compuesta y se pretende utilizar dos palabras.

 También puede agregar palabras compuestas a un diccionario personalizado para el corrector ortográfico. Palabras en el diccionario personalizado no causan infracciones. Para obtener más información, consulte [Cómo: personalizar el diccionario de análisis de código](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="related-rules"></a>Reglas relacionadas
 [CA1702: En las palabras compuestas se deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

 [CA1709: Los identificadores deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Los identificadores se deberían diferenciar en algo más que en el uso de mayúsculas y minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>Vea también
 [Convenciones de mayúsculas y minúsculas](http://msdn.microsoft.com/library/4c4ea526-9203-486f-b72d-29d61c5b3c6d) [directrices de nomenclatura](http://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3)



