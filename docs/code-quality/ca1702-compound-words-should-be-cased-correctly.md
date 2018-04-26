---
title: 'CA1702: En las palabras compuestas se deberían utilizar las mayúsculas y minúsculas correctamente'
ms.date: 03/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4703c43c81df13432f45fb4ba519a02b39a839e0
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="ca1702-compound-words-should-be-cased-correctly"></a>CA1702: En las palabras compuestas se deberían utilizar las mayúsculas y minúsculas correctamente

|||
|-|-|
|TypeName|CompoundWordsShouldBeCasedCorrectly|
|Identificador de comprobación|CA1702|
|Categoría|Microsoft.Naming|
|Cambio problemático|Importante cuando se desencadena en los ensamblados.<br /><br /> Poco problemático: cuando se desencadena en parámetros de tipo.|

## <a name="cause"></a>Motivo

El nombre de un identificador contiene varias palabras y al menos una de ellas parece ser una palabra compuesta en la que no se utilizan correctamente las mayúsculas y minúsculas.

## <a name="rule-description"></a>Descripción de la regla

El nombre del identificador se divide en palabras que se basan en las mayúsculas y minúsculas. La biblioteca de correctores ortográficos de Microsoft comprueba cada combinación de dos palabras contigua. Si se reconoce, el identificador genera una infracción de la regla. Ejemplos de palabras compuestas que producen una infracción son "CheckSum" y "MultiPart", que debe escribirse como "Checksum" y "Multipart", respectivamente. Debido a un uso común anterior, se generan varias excepciones en la regla, y se marcan algunas palabras únicas, como "Toolbar" y "Filename", que deberían escribirse como dos palabras distintas (en este caso, "ToolBar" y "FileName").

Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime. Esto reduce la curva de aprendizaje necesaria para las nuevas bibliotecas de software y aumenta la confianza del cliente respecto a que la biblioteca se haya desarrollado por parte de un especialista en desarrollo de código administrado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Cambie el nombre para que lo es mayúsculas y minúsculas correctamente.

## <a name="language"></a>Lenguaje

El corrector ortográfico comprueba actualmente solo con los diccionarios de la referencia cultural basada en inglés. Puede cambiar la referencia cultural del proyecto en el archivo de proyecto, agregando la **CodeAnalysisCulture** elemento.

Por ejemplo:

```xml
<Project ...>
  <PropertyGroup>
    <CodeAnalysisCulture>en-AU</CodeAnalysisCulture>
```

> [!IMPORTANT]
> Si establece la referencia cultural a algo distinto de una referencia cultural basada en inglés, esta regla de análisis de código está deshabilitada en modo silencioso.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Es seguro suprimir una advertencia de esta regla si ambas partes de la palabra compuesta se reconocen por el diccionario de ortografía y la intención es usar dos o más palabras.

## <a name="related-rules"></a>Reglas relacionadas

- [CA1701: En las palabras compuestas de la cadena de recursos se deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1709: Los identificadores deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Los identificadores se deberían diferenciar en algo más que en el uso de mayúsculas y minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>Vea también

- [Instrucciones de nomenclatura](/dotnet/standard/design-guidelines/naming-guidelines)
- [Convenciones sobre el uso de minúsculas y mayúsculas](/dotnet/standard/design-guidelines/capitalization-conventions)