---
title: 'CA1703: La ortografía de las cadenas de recursos debe ser correcta'
ms.date: 03/28/2018
ms.topic: reference
f1_keywords:
- ResourceStringsShouldBeSpelledCorrectly
- CA1703
helpviewer_keywords:
- CA1703
- ResourceStringsShouldBeSpelledCorrectly
ms.assetid: 693f4970-f512-40cb-ae3b-a0f3a5c6d6f1
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2643ff7cb8ce401462be7e5c1e52d5f985896f3a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546276"
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703: La ortografía de las cadenas de recursos debe ser correcta

|||
|-|-|
|TypeName|ResourceStringsShouldBeSpelledCorrectly|
|Identificador de comprobación|CA1703|
|Categoría|Microsoft.Naming|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo

Una cadena de recurso contiene una o varias palabras que la biblioteca de correctores ortográficos de Microsoft no reconoce.

## <a name="rule-description"></a>Descripción de la regla

Esta regla analiza la cadena de recurso en palabras (convirtiendo las palabras compuestas en tokens) y comprueba la ortografía de cada palabra o token. Para obtener información sobre el algoritmo de análisis, consulte [CA1704: Deben escribir correctamente los identificadores](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, utilice palabras completas que estén escritas correctamente o agregue las palabras a un diccionario personalizado. Para obtener información sobre cómo utilizar diccionarios personalizados, vea [CA1704: Deben escribir correctamente los identificadores](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="change-the-dictionary-language"></a>Cambiar el idioma del diccionario

De forma predeterminada, se utiliza la versión inglesa (en) del corrector ortográfico. Si desea cambiar el idioma del corrector ortográfico, puede hacerlo mediante la adición de uno de los siguientes atributos a la *AssemblyInfo.cs* o *AssemblyInfo.vb* archivo:

- Use <xref:System.Reflection.AssemblyCultureAttribute> para especificar la referencia cultural, si los recursos están en un ensamblado satélite.
- Uso <xref:System.Resources.NeutralResourcesLanguageAttribute> para especificar el *referencia cultural neutra* del ensamblado si los recursos están en el mismo ensamblado que el código.

> [!IMPORTANT]
> Si la referencia cultural se establece en algo distinto de una referencia cultural de inglés, esta regla de análisis de código se deshabilita de forma silenciosa.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

No suprima las advertencias de esta regla. Palabras escritas correctamente reducen el tiempo necesario para aprender nuevas bibliotecas de software.

## <a name="related-rules"></a>Reglas relacionadas

- [CA1701: Palabras compuestas de la cadena de recursos deberían escribirse correctamente](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1704: Los identificadores deberían tener la ortografía correcta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA2204: Deben escribir correctamente los literales](../code-quality/ca2204-literals-should-be-spelled-correctly.md)