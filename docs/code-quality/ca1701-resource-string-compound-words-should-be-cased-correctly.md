---
title: 'CA1701: Palabras compuestas de la cadena de recurso deben ser mayúsculas y minúsculas correctamente | Documentos de Microsoft'
ms.date: 03/28/2018
ms.technology: vs-ide-code-analysis
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
ms.openlocfilehash: 3d2579d50c6a82b4a2fdecaafbc43a904fd371ba
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
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

## <a name="change-the-dictionary-language"></a>Cambiar el idioma de diccionario

De forma predeterminada, se utiliza la versión de inglés (en) del corrector ortográfico. Si desea cambiar el idioma del corrector ortográfico, puede hacerlo mediante la adición de uno de los siguientes atributos a la *AssemblyInfo.cs* o *AssemblyInfo.vb* archivo:

- Use <xref:System.Reflection.AssemblyCultureAttribute> para especificar la referencia cultural, si los recursos se encuentran en un ensamblado satélite.
- Use <xref:System.Resources.NeutralResourcesLanguageAttribute> para especificar el *referencia cultural neutra* del ensamblado si los recursos están en el mismo ensamblado que el código.

> [!IMPORTANT]
> Si establece la referencia cultural a algo distinto de una referencia cultural basada en inglés, esta regla de análisis de código está deshabilitada en modo silencioso.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Es seguro suprimir una advertencia de esta regla si ambas partes de la palabra compuesta se reconocen por el diccionario de ortografía y la intención es usar dos o más palabras.

También puede agregar palabras compuestas a un diccionario personalizado para el corrector ortográfico. Las palabras en el diccionario personalizado no producen infracciones. Para obtener más información, consulte [Cómo: personalizar el diccionario de análisis de código](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="related-rules"></a>Reglas relacionadas

- [CA1702: En las palabras compuestas se deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)
- [CA1709: Los identificadores deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Los identificadores se deberían diferenciar en algo más que en el uso de mayúsculas y minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>Vea también

- [Convenciones sobre el uso de minúsculas y mayúsculas](/dotnet/standard/design-guidelines/capitalization-conventions)
- [Instrucciones de nomenclatura](/dotnet/standard/design-guidelines/naming-guidelines)