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
ms.openlocfilehash: edd3945953a07b10aee5c2690a25aafe446e2c10
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234321"
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703: La ortografía de las cadenas de recursos debe ser correcta

|||
|-|-|
|TypeName|ResourceStringsShouldBeSpelledCorrectly|
|Identificador de comprobación|CA1703|
|Categoría|Microsoft.Naming|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo

Una cadena de recurso contiene una o varias palabras que la biblioteca de correctores ortográficos de Microsoft no reconoce.

## <a name="rule-description"></a>Descripción de la regla

Esta regla analiza la cadena de recursos en palabras (con tokens compuestos de palabras compuestas) y comprueba la ortografía de cada palabra o token. Para obtener información sobre el algoritmo de análisis [, consulte CA1704: Los identificadores deben estar escritos correctamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, use palabras completas que estén escritas correctamente o agregue las palabras a un diccionario personalizado. Para obtener información sobre cómo usar diccionarios personalizados, vea [CA1704: Los identificadores deben estar escritos correctamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="change-the-dictionary-language"></a>Cambiar el idioma del Diccionario

De forma predeterminada, se usa la versión en inglés (en) del corrector ortográfico. Si desea cambiar el idioma del corrector ortográfico, puede hacerlo agregando uno de los siguientes atributos al archivo *AssemblyInfo.CS* o *AssemblyInfo. VB* :

- Utilice <xref:System.Reflection.AssemblyCultureAttribute> para especificar la referencia cultural si los recursos están en un ensamblado satélite.
- Utilice <xref:System.Resources.NeutralResourcesLanguageAttribute> para especificar la *referencia cultural neutra* del ensamblado si los recursos se encuentran en el mismo ensamblado que el código.

> [!IMPORTANT]
> Si establece la referencia cultural en algo distinto de una referencia cultural basada en inglés, esta regla de análisis de código se deshabilita de forma silenciosa.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

No suprima las advertencias de esta regla. Las palabras escritas correctamente reducen el tiempo necesario para obtener información sobre las nuevas bibliotecas de software.

## <a name="related-rules"></a>Reglas relacionadas

- [CA1701: Las palabras compuestas de cadena de recurso deben tener mayúsculas y minúsculas](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1704: Los identificadores deben estar escritos correctamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA2204: Los literales deben estar escritos correctamente](../code-quality/ca2204-literals-should-be-spelled-correctly.md)