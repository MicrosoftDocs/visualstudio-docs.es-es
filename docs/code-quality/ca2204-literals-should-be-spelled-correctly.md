---
title: 'CA2204: Deben escribir correctamente los literales | Documentos de Microsoft'
ms.date: 03/28/2018
ms.technology: vs-ide-code-analysis
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
ms.openlocfilehash: 8b57f4b30ffcebf6c51aa8741a21392ea29719a3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204: Debe escribir correctamente los literales

|||
|-|-|
|TypeName|LiteralsShouldBeSpelledCorrectly|
|Identificador de comprobación|CA2204|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo

Una cadena literal se pasa como argumento para un parámetro localizable, o a una propiedad traducible y la cadena contiene una o varias palabras que no son reconocidas por la biblioteca de correctores ortográficos de Microsoft.

## <a name="rule-description"></a>Descripción de la regla

Esta regla comprueba si una cadena literal que se pasa como un valor a un parámetro o una propiedad cuando uno o varios de los casos siguientes es true:

- El <xref:System.ComponentModel.LocalizableAttribute> del parámetro o la propiedad está establecido en true.

- El nombre de parámetro o la propiedad contiene "Text", "Mensaje" o "Título".

- El nombre de la variable de cadena que se pasa a un <xref:System.Console.Write%2A> o <xref:System.Console.WriteLine> método es "value" o "format".

Esta regla analiza la cadena literal en palabras, convirtiendo las palabras compuestas, tokens y comprueba la ortografía de cada palabra o token. Para obtener información sobre el algoritmo de análisis, consulte [CA1704: los identificadores deberían tener la ortografía correcta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

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

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, corrija la ortografía de la palabra o agregue la palabra a un diccionario personalizado. Para obtener información sobre cómo usar los diccionarios personalizados, vea [Cómo: personalizar el diccionario de análisis de código](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

No suprima las advertencias de esta regla. Palabras escritas correctamente reducen la curva de aprendizaje necesaria para las nuevas bibliotecas de software.

## <a name="related-rules"></a>Reglas relacionadas

- [CA1704: Los identificadores deberían tener la ortografía correcta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA1703: Las cadenas de recursos deberían tener la ortografía correcta](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)