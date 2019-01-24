---
title: 'CA2204: Los literales deben estar escritos correctamente'
ms.date: 03/28/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- Literals should be spelled correctly
- CA2204
- LiteralsShouldBeSpelledCorrectly
helpviewer_keywords:
- CA2204
ms.assetid: b0bbcbb6-c92d-4c14-8ef7-9c8b38c791a6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e23ab1c1c245a03e88b05fb15259193bb508b69a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53944316"
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204: Los literales deben estar escritos correctamente

|||
|-|-|
|TypeName|LiteralsShouldBeSpelledCorrectly|
|Identificador de comprobación|CA2204|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo

Una cadena literal se pasa como argumento para un parámetro localizable, o a una propiedad traducible y la cadena contiene una o varias palabras que no son reconocidas por la biblioteca de correctores ortográficos de Microsoft.

## <a name="rule-description"></a>Descripción de la regla

Esta regla comprueba si una cadena literal que se pasa como un valor a un parámetro o propiedad cuando uno o varios de los casos siguientes es true:

- El <xref:System.ComponentModel.LocalizableAttribute> atributo del parámetro o la propiedad se establece en true.

- El nombre de parámetro o la propiedad contiene "Text", "Mensaje" o "Título".

- El nombre de la variable de cadena que se pasa a un <xref:System.Console.Write%2A> o <xref:System.Console.WriteLine> método es "value" o "format".

Esta regla analiza la cadena literal en palabras, dividir en tokens las palabras compuestas y comprueba la ortografía de cada palabra o token. Para obtener información sobre el algoritmo de análisis, consulte [CA1704: Deben escribir correctamente los identificadores](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

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

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, corrija la ortografía de la palabra o agregar la palabra a un diccionario personalizado. Para obtener información sobre cómo usar los diccionarios personalizados, vea [Cómo: Personalizar el diccionario de análisis de código](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

No suprima las advertencias de esta regla. Palabras escritas correctamente reducen la curva de aprendizaje necesaria para las nuevas bibliotecas de software.

## <a name="related-rules"></a>Reglas relacionadas

- [CA1704: Los identificadores deberían tener la ortografía correcta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA1703: Cadenas de recursos deberían tener la ortografía correcta](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)