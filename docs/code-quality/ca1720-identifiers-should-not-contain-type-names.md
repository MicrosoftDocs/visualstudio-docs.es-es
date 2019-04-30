---
title: 'CA1720: Los identificadores no deben contener nombres de tipo'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1720
- IdentifiersShouldNotContainTypeNames
helpviewer_keywords:
- IdentifiersShouldNotContainTypeNames
- CA1720
ms.assetid: c95ee48f-f23a-45f0-ac9e-a3c1ecfabdea
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d0eb7cfeb2271b7ed01f59d4892987fb2ef72808
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546575"
---
# <a name="ca1720-identifiers-should-not-contain-type-names"></a>CA1720: Los identificadores no deben contener nombres de tipo

|||
|-|-|
|TypeName|IdentifiersShouldNotContainTypeNames|
|Identificador de comprobación|CA1720|
|Categoría|Microsoft.Naming|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo

El nombre de un parámetro en un miembro contiene un nombre de tipo de datos.

-o bien-

El nombre de un miembro contiene un nombre de tipo de datos específico del lenguaje.

De forma predeterminada, esta regla solo se examina los miembros visibles externamente, pero se trata de [configurable](#configurability).

## <a name="rule-description"></a>Descripción de la regla

Nombres de parámetros y miembros se usan mejor para comunicar su significado que to describir sus tipos, que se espera que se proporcionan herramientas de desarrollo. Para los nombres de miembros, si se debe usar un nombre de tipo de datos, use un nombre independiente del lenguaje en lugar de una específica del lenguaje. Por ejemplo, en lugar de la C# nombre de tipo `int`, utilice el nombre de tipo de datos independiente del lenguaje, `Int32`.

Cada token que conforma el nombre del parámetro o el miembro se compara con los siguientes nombres de tipo de datos específico del lenguaje de mayúsculas y minúsculas:

- Bool
- WChar
- Int8
- UInt8
- Short
- UShort
- Valor int.
- UInt
- Integer
- UInteger
- Long
- ULong
- Sin signo
- Firmado
- Float
- Float32
- Float64

Además, los nombres de parámetro también se comprueban con los siguientes nombres de tipo de datos independiente del lenguaje en mayúsculas y minúsculas:

- Object
- Obj
- Booleano
- Char
- String
- SByte
- Byte
- UByte
- Int16
- UInt16
- Int32
- UInt32
- Int64
- UInt64
- IntPtr
- Ptr
- Puntero
- UInptr
- UPtr
- UPointer
- Single
- Doble
- Decimal
- GUID

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

**Si se produce en un parámetro:**

Reemplace el identificador de tipo de datos en el nombre del parámetro con un término que mejor describe su significado o un término más genérico, como 'value'.

**Si se produce en un miembro:**

Reemplace el identificador de tipo de datos específico del lenguaje en el nombre del miembro con un término que mejor describe su significado, un equivalente independiente del lenguaje o un término más genérico, como 'value'.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

El uso ocasional de nombres de parámetros y miembros basados en tipos sean adecuado. Sin embargo, para el desarrollo nuevo, no conocidos se producen escenarios donde se debe suprimir una advertencia de esta regla. Para las bibliotecas que se han enviado anteriormente, es posible que deba suprimir una advertencia de esta regla.

## <a name="configurability"></a>Capacidad de configuración

Si ejecuta esta regla de [analizadores de FxCop](install-fxcop-analyzers.md) (y no a través de análisis de código estático), puede configurar qué partes de su código base para ejecutar esta regla en, en función de su accesibilidad. Por ejemplo, para especificar que debe ejecutarse la regla sólo con respecto a la superficie de API no públicos, agregue el siguiente par clave-valor a un archivo .editorconfig en el proyecto:

```
dotnet_code_quality.ca1720.api_surface = private, internal
```

Puede configurar esta opción para simplemente esta regla, para todas las reglas o para todas las reglas de esta categoría (convenciones de nomenclatura). Para obtener más información, consulte [analizadores de FxCop configurar](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Reglas relacionadas

- [CA1709: Los identificadores deberían escribirse correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Los identificadores deben diferenciarse por algo más que el caso](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
- [CA1707: Los identificadores no deberían contener subrayado](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)
- [CA1719: Los nombres de parámetro no deberían coincidir con los nombres de los miembros](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)