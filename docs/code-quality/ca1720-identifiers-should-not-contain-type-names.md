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
ms.openlocfilehash: a35bec2395ccec649443df71e87904c71bf635d8
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547100"
---
# <a name="ca1720-identifiers-should-not-contain-type-names"></a>CA1720: Los identificadores no deben contener nombres de tipo

|||
|-|-|
|TypeName|IdentifiersShouldNotContainTypeNames|
|Identificador de comprobación|CA1720|
|Categoría|Microsoft.Naming|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa

El nombre de un parámetro de un miembro contiene un nombre de tipo de datos.

-o bien-

El nombre de un miembro contiene un nombre de tipo de datos específico del idioma.

De forma predeterminada, esta regla solo examina los miembros visibles externamente, pero esto es [configurable](#configurability).

## <a name="rule-description"></a>Descripción de la regla

Los nombres de los parámetros y los miembros se utilizan mejor para comunicar su significado que describir su tipo, que se espera que proporcionen las herramientas de desarrollo. En el caso de los nombres de los miembros, si se debe usar un nombre de tipo de datos, use un nombre independiente del lenguaje en lugar de uno específico del lenguaje. Por ejemplo, en lugar del nombre C# `int`de tipo, use el nombre del tipo de datos independiente del `Int32`lenguaje,.

Los tokens discretos en el nombre del parámetro o miembro se comprueban con los siguientes nombres de tipos de datos específicos del lenguaje sin distinguir entre mayúsculas y minúsculas:

- Bool
- WChar
- Int8
- UInt8
- Breve
- UShort
- Int
- UInt
- Entero
- UInteger
- long
- ULong
- Sin signo
- Firmado
- Float
- Float32
- Float64

Además, los nombres de un parámetro también se comprueban con los siguientes nombres de tipos de datos independientes del lenguaje sin distinguir entre mayúsculas y minúsculas:

- Object
- Obj
- Boolean
- Char
- Cadena
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
- Double
- Decimal
- Guid

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

**Si se desencadena en un parámetro:**

Reemplace el identificador de tipo de datos en el nombre del parámetro por un término que describa mejor su significado o un término más genérico, como ' valor '.

**Si se desencadena en un miembro:**

Reemplace el identificador de tipo de datos específico del lenguaje en el nombre del miembro por un término que describa mejor su significado, un equivalente independiente del lenguaje o un término más genérico, como ' valor '.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

El uso ocasional de los nombres de los parámetros y miembros basados en tipos puede ser adecuado. Sin embargo, para el nuevo desarrollo, no se produce ningún escenario conocido en el que debe suprimir una advertencia de esta regla. En el caso de las bibliotecas que se hayan enviado anteriormente, es posible que tenga que suprimir una advertencia de esta regla.

## <a name="configurability"></a>Configurabilidad

Si está ejecutando esta regla desde los [analizadores de FxCop](install-fxcop-analyzers.md) (y no con el análisis heredado), puede configurar en qué partes del código base ejecutar esta regla, según su accesibilidad. Por ejemplo, para especificar que la regla se debe ejecutar solo en la superficie de API no pública, agregue el siguiente par clave-valor a un archivo. editorconfig en el proyecto:

```ini
dotnet_code_quality.ca1720.api_surface = private, internal
```

Puede configurar esta opción solo para esta regla, para todas las reglas o para todas las reglas de esta categoría (nomenclatura). Para obtener más información, vea [configurar analizadores de FxCop](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Reglas relacionadas

- [CA1709: Los identificadores deben usar mayúsculas y minúsculas correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Los identificadores deben diferir más que el uso de mayúsculas y minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
- [CA1707: Los identificadores no deben contener guiones bajos](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)
- [CA1719: Los nombres de parámetro no deben coincidir con los nombres de miembro](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)