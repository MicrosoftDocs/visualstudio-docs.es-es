---
title: 'CA1701: En las palabras compuestas de la cadena de recursos se deben utilizar mayúsculas y minúsculas correctamente'
ms.date: 03/28/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- ResourceStringCompoundWordsShouldBeCasedCorrectly
- CA1701
helpviewer_keywords:
- CA1701
- ResourceStringCompoundWordsShouldBeCasedCorrectly
ms.assetid: 4ddbe09f-24b8-4c47-9373-a06f4487ca0d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e2cc74bb7d3cc15e593d465a8c8d0d55275954ff
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53841786"
---
# <a name="ca1701-resource-string-compound-words-should-be-cased-correctly"></a>CA1701: En las palabras compuestas de la cadena de recursos se deben utilizar mayúsculas y minúsculas correctamente

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

## <a name="change-the-dictionary-language"></a>Cambiar el idioma del diccionario

De forma predeterminada, se utiliza la versión inglesa (en) del corrector ortográfico. Si desea cambiar el idioma del corrector ortográfico, puede hacerlo mediante la adición de uno de los siguientes atributos a la *AssemblyInfo.cs* o *AssemblyInfo.vb* archivo:

- Use <xref:System.Reflection.AssemblyCultureAttribute> para especificar la referencia cultural, si los recursos están en un ensamblado satélite.
- Uso <xref:System.Resources.NeutralResourcesLanguageAttribute> para especificar el *referencia cultural neutra* del ensamblado si los recursos están en el mismo ensamblado que el código.

> [!IMPORTANT]
> Si la referencia cultural se establece en algo distinto de una referencia cultural de inglés, esta regla de análisis de código se deshabilita de forma silenciosa.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Es seguro suprimir una advertencia de esta regla si el diccionario ortográfico reconoce ambas partes de la palabra compuesta y se pretende utilizar dos palabras.

También puede agregar palabras compuestas a un diccionario personalizado para el corrector ortográfico. Palabras en el diccionario personalizado no causan infracciones. Para obtener más información, vea [Cómo: Personalizar el diccionario de análisis de código](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="related-rules"></a>Reglas relacionadas

- [CA1702: En las palabras compuestas se deberían escribirse correctamente](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)
- [CA1709: Los identificadores deberían escribirse correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Los identificadores deben diferenciarse por algo más que el caso](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>Vea también

- [Convenciones sobre el uso de minúsculas y mayúsculas](/dotnet/standard/design-guidelines/capitalization-conventions)
- [Instrucciones de nomenclatura](/dotnet/standard/design-guidelines/naming-guidelines)