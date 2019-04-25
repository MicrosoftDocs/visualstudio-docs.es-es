---
title: 'CA1702: En las palabras compuestas se deben utilizar mayúsculas y minúsculas correctamente'
ms.date: 03/28/2018
ms.topic: reference
f1_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
helpviewer_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
ms.assetid: 05481245-7ad8-48c3-a456-3aa44b6160a6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f78ea4f44c48d2740df58def03a6335bce6637a2
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55942770"
---
# <a name="ca1702-compound-words-should-be-cased-correctly"></a>CA1702: En las palabras compuestas se deben utilizar mayúsculas y minúsculas correctamente

|||
|-|-|
|TypeName|CompoundWordsShouldBeCasedCorrectly|
|Identificador de comprobación|CA1702|
|Categoría|Microsoft.Naming|
|Cambio problemático|Importante cuando se desencadena en ensamblados.<br /><br /> Indivisible: cuando se desencadena en parámetros de tipo.|

## <a name="cause"></a>Motivo

El nombre de un identificador contiene varias palabras y al menos una de ellas parece ser una palabra compuesta en la que no se utilizan correctamente las mayúsculas y minúsculas.

## <a name="rule-description"></a>Descripción de la regla

El nombre del identificador se divide en palabras que se basan en las mayúsculas y minúsculas. La biblioteca de correctores ortográficos de Microsoft comprueba cada combinación de dos palabras contigua. Si lo reconoce, el identificador genera una infracción de la regla. Ejemplos de palabras compuestas que originan una infracción son "CheckSum" y "MultiPart", que debería escribirse como "Checksum" y "Multipart", respectivamente. Debido al uso común anterior, se generan varias excepciones a la regla, y se marcan algunas palabras únicas, como "Toolbar" y "Filename", que deberían escribirse como dos palabras distintas (en este caso, "ToolBar" y "FileName").

Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime. Esto reduce la curva de aprendizaje necesaria para las nuevas bibliotecas de software y aumenta la confianza del cliente respecto a que la biblioteca se haya desarrollado por parte de un especialista en desarrollo de código administrado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Cambie el nombre por lo que es con grafía correctamente.

## <a name="language"></a>Lenguaje

El corrector ortográfico comprueba actualmente sólo con los diccionarios de la referencia cultural en inglés. Puede cambiar la referencia cultural de su proyecto en el archivo de proyecto, agregando la **CodeAnalysisCulture** elemento.

Por ejemplo:

```xml
<Project ...>
  <PropertyGroup>
    <CodeAnalysisCulture>en-AU</CodeAnalysisCulture>
```

> [!IMPORTANT]
> Si la referencia cultural se establece en algo distinto de una referencia cultural de inglés, esta regla de análisis de código se deshabilita de forma silenciosa.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Es seguro suprimir una advertencia de esta regla si el diccionario ortográfico reconoce ambas partes de la palabra compuesta y se pretende utilizar dos palabras.

## <a name="related-rules"></a>Reglas relacionadas

- [CA1701: Palabras compuestas de la cadena de recursos deberían escribirse correctamente](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1709: Los identificadores deberían escribirse correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Los identificadores deben diferenciarse por algo más que el caso](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>Vea también

- [Instrucciones de nomenclatura](/dotnet/standard/design-guidelines/naming-guidelines)
- [Convenciones sobre el uso de minúsculas y mayúsculas](/dotnet/standard/design-guidelines/capitalization-conventions)