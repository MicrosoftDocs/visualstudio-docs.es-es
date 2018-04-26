---
title: 'CA1703: Las cadenas de recursos deberían tener la ortografía correcta'
ms.date: 03/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e8103353fc5d2e0d74b5355259f0e2bc77ddd974
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703: Las cadenas de recursos deberían tener la ortografía correcta

|||
|-|-|
|TypeName|ResourceStringsShouldBeSpelledCorrectly|
|Identificador de comprobación|CA1703|
|Categoría|Microsoft.Naming|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo

Una cadena de recurso contiene una o varias palabras que la biblioteca de correctores ortográficos de Microsoft no reconoce.

## <a name="rule-description"></a>Descripción de la regla

Esta regla analiza la cadena de recurso en palabras (dividir palabras compuestas en tokens) y comprueba la ortografía de cada palabra o token. Para obtener información sobre el algoritmo de análisis, consulte [CA1704: los identificadores deberían tener la ortografía correcta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, utilice palabras completas que se ha escrito correctamente o agregar las palabras a un diccionario personalizado. Para obtener información sobre cómo usar los diccionarios personalizados, vea [CA1704: los identificadores deberían tener la ortografía correcta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="change-the-dictionary-language"></a>Cambiar el idioma de diccionario

De forma predeterminada, se utiliza la versión de inglés (en) del corrector ortográfico. Si desea cambiar el idioma del corrector ortográfico, puede hacerlo mediante la adición de uno de los siguientes atributos a la *AssemblyInfo.cs* o *AssemblyInfo.vb* archivo:

- Use <xref:System.Reflection.AssemblyCultureAttribute> para especificar la referencia cultural, si los recursos se encuentran en un ensamblado satélite.
- Use <xref:System.Resources.NeutralResourcesLanguageAttribute> para especificar el *referencia cultural neutra* del ensamblado si los recursos están en el mismo ensamblado que el código.

> [!IMPORTANT]
> Si establece la referencia cultural a algo distinto de una referencia cultural basada en inglés, esta regla de análisis de código está deshabilitada en modo silencioso.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

No suprima las advertencias de esta regla. Palabras escritas correctamente reducen el tiempo necesario para obtener información sobre nuevas bibliotecas de software.

## <a name="related-rules"></a>Reglas relacionadas

- [CA1701: En las palabras compuestas de la cadena de recursos se deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1704: Los identificadores deberían tener la ortografía correcta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA2204: Los literales deben estar escritos correctamente ](../code-quality/ca2204-literals-should-be-spelled-correctly.md)