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
ms.openlocfilehash: 4bb79d2944bdb49c59fd53fb30e1497c57c5c516
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62779657"
---
# <a name="ca1008-enums-should-have-zero-value"></a>CA1008: Las enumeraciones deben tener un valor igual a cero

|||
|-|-|
|TypeName|EnumsShouldHaveZeroValue|
|Identificador de comprobación|CA1008|
|Categoría|Microsoft.Design|
|Cambio problemático|No problemático: cuando se le pida que agregue un **ninguno** valor a una enumeración sin marca. Problemático: cuando se le pedirá que cambie el nombre o quitar cualquier valor de enumeración.|

## <a name="cause"></a>Motivo

Una enumeración sin un aplicada <xref:System.FlagsAttribute?displayProperty=fullName> no define un miembro que tiene un valor de cero. O bien, una enumeración que tiene un aplicada <xref:System.FlagsAttribute> define un miembro que tiene un valor de cero pero su nombre no es 'None'. O bien, la enumeración define varios miembros con valor cero.

De forma predeterminada, esta regla solo se examina las enumeraciones visibles externamente, pero se trata de [configurable](#configurability).

## <a name="rule-description"></a>Descripción de la regla

El valor predeterminado de una enumeración no inicializada, igual que otros tipos de valor, es cero. Una enumeración sin atributos marcadores debería definir a un miembro que tiene el valor de cero para que el valor predeterminado es un valor válido de la enumeración. Si es necesario, el nombre del miembro 'None'. De lo contrario, asigna el valor cero para el miembro que se usan con más frecuencia. De forma predeterminada, si el valor del primer miembro de enumeración no se establece en la declaración, su valor es cero.

Si una enumeración que tiene el <xref:System.FlagsAttribute> aplicado define un miembro con valor cero, su nombre debe ser 'None' para indicar que no se ha establecido ningún valor en la enumeración. Uso de un miembro con valor cero para cualquier otro propósito es contrario a la utilización de la <xref:System.FlagsAttribute> en que la operación AND y o los operadores bit a bit son útiles con el miembro. Esto implica que solo un miembro debe tener asignado el valor cero. Si se producen varios miembros que tienen el valor cero en una enumeración con atributos de marcas, `Enum.ToString()` devuelve resultados incorrectos para los miembros que no son cero.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla para las enumeraciones sin atributos de marcas, definir a un miembro que tiene el valor de cero; se trata de un cambio sin interrupción. Para las enumeraciones con atributos de marcas que definen a un miembro con valor cero, denomine al miembro 'None' y eliminar a todos los miembros que tienen un valor de cero; se trata de un cambio importante.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

No suprima una advertencia de esta regla excepto para atribuyen en indicadores enumeraciones que anteriormente se han enviado.

## <a name="configurability"></a>Capacidad de configuración

Si ejecuta esta regla de [analizadores de FxCop](install-fxcop-analyzers.md) (y no a través de análisis de código estático), puede configurar qué partes de su código base para ejecutar esta regla en, en función de su accesibilidad. Por ejemplo, para especificar que debe ejecutarse la regla sólo con respecto a la superficie de API no públicos, agregue el siguiente par clave-valor a un archivo .editorconfig en el proyecto:

```
dotnet_code_quality.ca1008.api_surface = private, internal
```

Puede configurar esta opción para simplemente esta regla, para todas las reglas o para todas las reglas de esta categoría (diseño). Para obtener más información, consulte [analizadores de FxCop configurar](configure-fxcop-analyzers.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra dos enumeraciones que cumplen la regla y una enumeración, `BadTraceOptions`, que infringe la regla.

[!code-cpp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CPP/ca1008-enums-should-have-zero-value_1.cpp)]
[!code-csharp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CSharp/ca1008-enums-should-have-zero-value_1.cs)]
[!code-vb[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/VisualBasic/ca1008-enums-should-have-zero-value_1.vb)]

## <a name="related-rules"></a>Reglas relacionadas

- [CA2217: No marcar enumeraciones con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)
- [CA1700: No nombrar valores de enumeración 'Reserved'](../code-quality/ca1700-do-not-name-enum-values-reserved.md)
- [CA1712: No utilizar prefijos en valores de enumeración con el nombre de tipo](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)
- [CA1028: Almacenamiento de enum debe ser Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)
- [CA1027: Marcar enumeraciones con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Vea también

- <xref:System.Enum?displayProperty=fullName>