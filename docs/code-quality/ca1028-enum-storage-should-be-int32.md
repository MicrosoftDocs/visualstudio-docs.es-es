---
title: 'CA1028: El almacenamiento de la enumeración debe ser de tipo Int32'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1028
- EnumStorageShouldBeInt32
helpviewer_keywords:
- EnumStorageShouldBeInt32
- CA1028
ms.assetid: 87160825-9f39-4142-8d7f-a31fe7ac7b84
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 95e2a8892bb7b52122dd34afa3f300123149bb26
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62779241"
---
# <a name="ca1028-enum-storage-should-be-int32"></a>CA1028: El almacenamiento de la enumeración debe ser de tipo Int32

|||
|-|-|
|TypeName|EnumStorageShouldBeInt32|
|Identificador de comprobación|CA1028|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo

El tipo subyacente de una enumeración no es <xref:System.Int32?displayProperty=fullName>.

De forma predeterminada, esta regla solo se examina enumeraciones públicas, pero se trata de [configurable](#configurability).

## <a name="rule-description"></a>Descripción de la regla

Una enumeración es un tipo de valor que define un conjunto de constantes con nombre relacionadas. De forma predeterminada, el <xref:System.Int32?displayProperty=fullName> tipo de datos se usa para almacenar el valor constante. Aunque puede cambiar este tipo subyacente, no es necesario ni recomendado para la mayoría de los escenarios. Ninguna mejora significativa del rendimiento se logra mediante el uso de un tipo de datos es menor que <xref:System.Int32>. Si no puede usar el tipo de datos de forma predeterminada, debe usar uno de los sistema de Common Language (CLS)-compatible con tipos enteros, <xref:System.Byte>, <xref:System.Int16>, <xref:System.Int32>, o <xref:System.Int64> para asegurarse de que todos los valores de la enumeración se pueden representar en Lenguajes de programación conforme a CLS.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, a menos que existan problemas de compatibilidad o tamaño, utilice <xref:System.Int32>. Para las situaciones donde <xref:System.Int32> no es lo suficientemente grande como para contener los valores, use <xref:System.Int64>. Si la compatibilidad con versiones anteriores requiere un tipo de datos más pequeño, utilice <xref:System.Byte> o <xref:System.Int16>.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Suprima una advertencia de esta regla solo si lo requieren los problemas de compatibilidad con versiones anteriores. En las aplicaciones, incumplimiento de esta regla normalmente no provoca problemas. En bibliotecas, donde se requiere la interoperabilidad entre lenguajes, incumplimiento de esta regla puede afectar negativamente a los usuarios.

## <a name="configurability"></a>Capacidad de configuración

Si ejecuta esta regla de [analizadores de FxCop](install-fxcop-analyzers.md) (y no a través de análisis de código estático), puede configurar qué partes de su código base para ejecutar esta regla en, en función de su accesibilidad. Por ejemplo, para especificar que debe ejecutarse la regla sólo con respecto a la superficie de API no públicos, agregue el siguiente par clave-valor a un archivo .editorconfig en el proyecto:

```
dotnet_code_quality.ca1028.api_surface = private, internal
```

Puede configurar esta opción para simplemente esta regla, para todas las reglas o para todas las reglas de esta categoría (diseño). Para obtener más información, consulte [analizadores de FxCop configurar](configure-fxcop-analyzers.md).

## <a name="example-of-a-violation"></a>Ejemplo de una infracción

El ejemplo siguiente muestra dos enumeraciones que no usan el tipo de datos subyacente recomendado.

[!code-vb[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_1.vb)]
[!code-csharp[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_1.cs)]

## <a name="example-of-how-to-fix"></a>Ejemplo de cómo corregir

En el ejemplo siguiente se corrige la infracción anterior cambiando el tipo de datos subyacente <xref:System.Int32>.

[!code-csharp[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_2.cs)]
[!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_2.vb)]

## <a name="related-rules"></a>Reglas relacionadas

- [CA1008: Las enumeraciones deben tener el valor cero](../code-quality/ca1008-enums-should-have-zero-value.md)
- [CA1027: Marcar enumeraciones con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)
- [CA2217: No marcar enumeraciones con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)
- [CA1700: No nombrar valores de enumeración 'Reserved'](../code-quality/ca1700-do-not-name-enum-values-reserved.md)
- [CA1712: No utilizar prefijos en valores de enumeración con el nombre de tipo](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

## <a name="see-also"></a>Vea también

- <xref:System.Byte?displayProperty=fullName>
- <xref:System.Int16?displayProperty=fullName>
- <xref:System.Int32?displayProperty=fullName>
- <xref:System.Int64?displayProperty=fullName>