---
title: 'CA1028: El almacenamiento de la enumeración debe ser de tipo Int32'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f0f9dec006f3684259541811e905eaf75a790c3a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31900293"
---
# <a name="ca1028-enum-storage-should-be-int32"></a>CA1028: El almacenamiento de la enumeración debe ser de tipo Int32
|||
|-|-|
|TypeName|EnumStorageShouldBeInt32|
|Identificador de comprobación|CA1028|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 El tipo subyacente de una enumeración pública no es <xref:System.Int32?displayProperty=fullName>.

## <a name="rule-description"></a>Descripción de la regla
 Una enumeración es un tipo de valor que define un conjunto de constantes con nombre relacionadas. De forma predeterminada, la <xref:System.Int32?displayProperty=fullName> tipo de datos se utiliza para almacenar el valor constante. Aunque puede cambiar este tipo subyacente, no es necesaria o recomendada para la mayoría de los escenarios. Tenga en cuenta que ninguna mejora significativa del rendimiento se logra mediante el uso de un tipo de datos que es menor que <xref:System.Int32>. Si no puede usar el tipo de datos de forma predeterminada, debería usar uno de sistema de lenguaje común (CLS)-compatible con tipos enteros, <xref:System.Byte>, <xref:System.Int16>, <xref:System.Int32>, o <xref:System.Int64> para asegurarse de que todos los valores de la enumeración se pueden representar en Lenguajes de programación compatibles con CLS.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, a menos que existan problemas de compatibilidad o tamaño, utilice <xref:System.Int32>. En situaciones donde <xref:System.Int32> no es lo suficientemente grande como para contener los valores, utilice <xref:System.Int64>. Si la compatibilidad con versiones anteriores requiere un tipo de datos más pequeño, utilice <xref:System.Byte> o <xref:System.Int16>.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Suprima las advertencias de esta regla sólo si así lo requieren los problemas de compatibilidad con versiones anteriores. En las aplicaciones, no cumplir esta regla normalmente no provoca problemas. En bibliotecas, donde se requiere la interoperabilidad entre lenguajes, no cumplir esta regla podría afectar negativamente a los usuarios.

## <a name="example-of-a-violation"></a>Ejemplo de una infracción

### <a name="description"></a>Descripción
 El ejemplo siguiente muestra dos enumeraciones que no utilizan el tipo de datos subyacente recomendado.

### <a name="code"></a>Código
 [!code-vb[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_1.vb)]
 [!code-csharp[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_1.cs)]

## <a name="example-of-how-to-fix"></a>Ejemplo de cómo reparar

### <a name="description"></a>Descripción
 En el ejemplo siguiente se corrige la infracción anterior cambiando el tipo de datos subyacente para <xref:System.Int32>.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_2.cs)]
 [!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_2.vb)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1008: Las enumeraciones deben tener un valor igual a cero](../code-quality/ca1008-enums-should-have-zero-value.md)

 [CA1027: Marcar enumeraciones con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: No marcar enumeraciones con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1700: No nombrar valores de enumeración como 'Reserved'](../code-quality/ca1700-do-not-name-enum-values-reserved.md)

 [CA1712: No utilizar prefijos en valores de enumeración con el nombre del tipo](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

## <a name="see-also"></a>Vea también
 <xref:System.Byte?displayProperty=fullName> <xref:System.Int16?displayProperty=fullName> <xref:System.Int32?displayProperty=fullName> <xref:System.Int64?displayProperty=fullName>