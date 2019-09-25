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
ms.openlocfilehash: 5480d3dde926dfe31b018a5cd0b1ea6a5813063b
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234337"
---
# <a name="ca1702-compound-words-should-be-cased-correctly"></a>CA1702: En las palabras compuestas se deben utilizar mayúsculas y minúsculas correctamente

|||
|-|-|
|TypeName|CompoundWordsShouldBeCasedCorrectly|
|Identificador de comprobación|CA1702|
|Categoría|Microsoft.Naming|
|Cambio importante|Problemático: cuando se desencadena en ensamblados.<br /><br /> No problemático: cuando se desencadena en parámetros de tipo.|

## <a name="cause"></a>Motivo

El nombre de un identificador contiene varias palabras y al menos una de ellas parece ser una palabra compuesta en la que no se utilizan correctamente las mayúsculas y minúsculas.

## <a name="rule-description"></a>Descripción de la regla

El nombre del identificador se divide en palabras que se basan en el uso de mayúsculas y minúsculas. La biblioteca del corrector ortográfico de Microsoft comprueba cada combinación de dos palabras contiguas. Si se reconoce, el identificador produce una infracción de la regla. Ejemplos de palabras compuestas que causan una infracción son "CheckSum" y "multipart", que deben usarse como "checksum" y "multipart", respectivamente. Debido al uso común anterior, hay varias excepciones integradas en la regla y se marcan varias palabras individuales, como "Toolbar" y "filename", que deben usarse como dos palabras distintas (en este caso, "ToolBar" y "FileName").

Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime. Esto reduce la curva de aprendizaje necesaria para las nuevas bibliotecas de software y aumenta la confianza del cliente respecto a que la biblioteca se haya desarrollado por parte de un especialista en desarrollo de código administrado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Cambie el nombre para que sea correcto.

## <a name="language"></a>Lenguaje

El corrector ortográfico comprueba actualmente únicamente los diccionarios de referencia cultural basados en inglés. Puede cambiar la referencia cultural del proyecto en el archivo del proyecto agregando el elemento **CodeAnalysisCulture** .

Por ejemplo:

```xml
<Project ...>
  <PropertyGroup>
    <CodeAnalysisCulture>en-AU</CodeAnalysisCulture>
```

> [!IMPORTANT]
> Si establece la referencia cultural en algo distinto de una referencia cultural basada en inglés, esta regla de análisis de código se deshabilita de forma silenciosa.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Es seguro suprimir una advertencia de esta regla si el diccionario ortográfico reconoce ambas partes de la palabra compuesta y el objetivo es usar dos palabras.

## <a name="related-rules"></a>Reglas relacionadas

- [CA1701: Las palabras compuestas de cadena de recurso deben tener mayúsculas y minúsculas](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1709: Los identificadores deben usar mayúsculas y minúsculas correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Los identificadores deben diferir más que el uso de mayúsculas y minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>Vea también

- [Instrucciones de nomenclatura](/dotnet/standard/design-guidelines/naming-guidelines)
- [Convenciones sobre el uso de minúsculas y mayúsculas](/dotnet/standard/design-guidelines/capitalization-conventions)