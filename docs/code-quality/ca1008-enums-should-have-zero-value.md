---
title: 'CA1008: Las enumeraciones deben tener un valor igual a cero'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1008
- EnumsShouldHaveZeroValue
helpviewer_keywords:
- CA1008
- EnumsShouldHaveZeroValue
ms.assetid: 3503a73c-360c-416d-8ee4-c2aa44365a05
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c9b6e48fb82be5a41c420827a32926630bb725ed
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236490"
---
# <a name="ca1008-enums-should-have-zero-value"></a>CA1008: Las enumeraciones deben tener un valor igual a cero

|||
|-|-|
|TypeName|EnumsShouldHaveZeroValue|
|Identificador de comprobación|CA1008|
|Categoría|Microsoft.Design|
|Cambio importante|Sin interrupciones: cuando se le pide que agregue un valor **None** a una enumeración sin marca. Interrumpir: cuando se le pida que cambie el nombre o quite los valores de enumeración.|

## <a name="cause"></a>Motivo

Una enumeración sin un <xref:System.FlagsAttribute?displayProperty=fullName> elemento aplicado no define ningún miembro que tenga un valor de cero. O bien, una enumeración que tiene <xref:System.FlagsAttribute> un aplicado define un miembro que tiene un valor de cero pero su nombre no es ' none '. O bien, la enumeración define varios miembros de valor cero.

De forma predeterminada, esta regla solo examina las enumeraciones visibles externamente, pero esto es [configurable](#configurability).

## <a name="rule-description"></a>Descripción de la regla

El valor predeterminado de una enumeración no inicializada, al igual que otros tipos de valor, es cero. Una enumeración con atributos sin marcas debe definir un miembro que tenga el valor de cero para que el valor predeterminado sea un valor válido de la enumeración. Si es necesario, asigne al miembro el nombre ' none '. De lo contrario, asigne cero al miembro usado con más frecuencia. De forma predeterminada, si el valor del primer miembro de la enumeración no se establece en la declaración, su valor es cero.

Si una enumeración que tiene <xref:System.FlagsAttribute> aplicado define un miembro con valor cero, su nombre debe ser ' none ' para indicar que no se ha establecido ningún valor en la enumeración. El uso de un miembro con valor cero para cualquier otro propósito es contrario al uso de <xref:System.FlagsAttribute> en que los operadores bit a and y or no son útiles con el miembro. Esto implica que solo un miembro debe tener asignado el valor cero. Si se producen varios miembros que tienen el valor cero en una enumeración con atributos `Enum.ToString()` de marcas, devuelve resultados incorrectos para los miembros que no son cero.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla para enumeraciones con atributos sin marcas, defina un miembro que tenga el valor cero; se trata de un cambio no problemático. En el caso de las enumeraciones con atributos de marcas que definen un miembro con valor cero, asigne un nombre a este miembro ' none ' y elimine cualquier otro miembro que tenga un valor de cero; se trata de un cambio importante.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

No suprima una advertencia de esta regla excepto para las enumeraciones con atributos de marcas que se hayan enviado previamente.

## <a name="configurability"></a>Configurabilidad

Si está ejecutando esta regla desde los [analizadores de FxCop](install-fxcop-analyzers.md) (y no con el análisis heredado), puede configurar en qué partes del código base ejecutar esta regla, según su accesibilidad. Por ejemplo, para especificar que la regla se debe ejecutar solo en la superficie de API no pública, agregue el siguiente par clave-valor a un archivo. editorconfig en el proyecto:

```ini
dotnet_code_quality.ca1008.api_surface = private, internal
```

Puede configurar esta opción solo para esta regla, para todas las reglas o para todas las reglas de esta categoría (diseño). Para obtener más información, vea [configurar analizadores de FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestran dos enumeraciones que cumplen la regla y una `BadTraceOptions`enumeración,, que infringe la regla.

[!code-cpp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CPP/ca1008-enums-should-have-zero-value_1.cpp)]
[!code-csharp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CSharp/ca1008-enums-should-have-zero-value_1.cs)]
[!code-vb[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/VisualBasic/ca1008-enums-should-have-zero-value_1.vb)]

## <a name="related-rules"></a>Reglas relacionadas

- [CA2217 No marcar enumeraciones con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)
- [CA1700: No asignar nombre a los valores de enumeración ' Reserved '](../code-quality/ca1700-do-not-name-enum-values-reserved.md)
- [CA1712: No Prefije valores de enumeración con el nombre de tipo](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)
- [CA1028: El almacenamiento de enumeración debe ser Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)
- [CA1027: Marcar enumeraciones con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Vea también

- <xref:System.Enum?displayProperty=fullName>