---
title: 'CA1028: el almacenamiento de la enumeración debe ser Int32 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1028
- EnumStorageShouldBeInt32
helpviewer_keywords:
- EnumStorageShouldBeInt32
- CA1028
ms.assetid: 87160825-9f39-4142-8d7f-a31fe7ac7b84
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: fc1039cb547a48c4f2dd3ea869b46d4706e9c3a2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661905"
---
# <a name="ca1028-enum-storage-should-be-int32"></a>CA1028: El almacenamiento de la enumeración debe ser de tipo Int32
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|EnumStorageShouldBeInt32|
|Identificador de comprobación|CA1028|
|Categoría|Microsoft. Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 No se <xref:System.Int32?displayProperty=fullName> el tipo subyacente de una enumeración pública.

## <a name="rule-description"></a>Descripción de la regla
 Una enumeración es un tipo de valor que define un conjunto de constantes con nombre relacionadas. De forma predeterminada, el tipo de datos <xref:System.Int32?displayProperty=fullName> se usa para almacenar el valor constante. Aunque puede cambiar este tipo subyacente, no es necesario ni se recomienda para la mayoría de los escenarios. Tenga en cuenta que no se consigue un aumento significativo del rendimiento mediante el uso de un tipo de datos menor que <xref:System.Int32>. Si no puede utilizar el tipo de datos predeterminado, debe usar uno de los tipos enteros conformes a Common Language System (CLS), <xref:System.Byte>, <xref:System.Int16>, <xref:System.Int32> o <xref:System.Int64> para asegurarse de que todos los valores de la enumeración se pueden representar en la programación conforme a CLS. Idiomas.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, a menos que existan problemas de tamaño o compatibilidad, use <xref:System.Int32>. En situaciones en las que <xref:System.Int32> no sea lo suficientemente grande como para contener los valores, use <xref:System.Int64>. Si la compatibilidad con versiones anteriores requiere un tipo de datos más pequeño, use <xref:System.Byte> o <xref:System.Int16>.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Suprima una advertencia de esta regla solo si los problemas de compatibilidad con versiones anteriores lo requieren. En las aplicaciones, si no se cumple esta regla normalmente no se producen problemas. En el caso de las bibliotecas, donde se requiere la interoperabilidad de lenguajes, el hecho de no cumplir esta regla podría afectar negativamente a los usuarios.

## <a name="example-of-a-violation"></a>Ejemplo de una infracción

### <a name="description"></a>Descripción
 En el ejemplo siguiente se muestran dos enumeraciones que no utilizan el tipo de datos subyacente recomendado.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Design.EnumIntegralType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralType/cs/FxCop.Design.EnumIntegralType.cs#1)]
 [!code-vb[FxCop.Design.EnumIntegralType#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralType/vb/FxCop.Design.EnumIntegralType.vb#1)]

## <a name="example-of-how-to-fix"></a>Ejemplo de cómo corregir

### <a name="description"></a>Descripción
 En el ejemplo siguiente se corrige la infracción anterior cambiando el tipo de datos subyacente a <xref:System.Int32>.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Design.EnumIntegralTypeFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralTypeFixed/cs/FxCop.Design.EnumIntegralTypeFixed.cs#1)]
 [!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralTypeFixed/vb/FxCop.Design.EnumIntegralTypeFixed.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1008: Las enumeraciones deben tener un valor igual a cero](../code-quality/ca1008-enums-should-have-zero-value.md)

 [CA1027: Marcar enumeraciones con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: No marcar enumeraciones con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1700: No nombrar valores de enumeración como 'Reserved'](../code-quality/ca1700-do-not-name-enum-values-reserved.md)

 [CA1712: No utilizar prefijos en valores de enumeración con el nombre del tipo](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

## <a name="see-also"></a>Vea también
 <xref:System.Byte?displayProperty=fullName> <xref:System.Int16?displayProperty=fullName>
 <xref:System.Int32?displayProperty=fullName>
 <xref:System.Int64?displayProperty=fullName>
