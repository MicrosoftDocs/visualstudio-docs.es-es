---
title: 'CA1028: Almacenamiento de la enumeración debe ser de tipo Int32 | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1028
- EnumStorageShouldBeInt32
helpviewer_keywords:
- EnumStorageShouldBeInt32
- CA1028
ms.assetid: 87160825-9f39-4142-8d7f-a31fe7ac7b84
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 9d5d3b42dc9880721e8e583a1402e56c242d5c47
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49892173"
---
# <a name="ca1028-enum-storage-should-be-int32"></a>CA1028: El almacenamiento de la enumeración debe ser de tipo Int32
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|EnumStorageShouldBeInt32|
|Identificador de comprobación|CA1028|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 El tipo subyacente de una enumeración pública no es <xref:System.Int32?displayProperty=fullName>.

## <a name="rule-description"></a>Descripción de la regla
 Una enumeración es un tipo de valor que define un conjunto de constantes con nombre relacionadas. De forma predeterminada, el <xref:System.Int32?displayProperty=fullName> tipo de datos se usa para almacenar el valor constante. Aunque puede cambiar este tipo subyacente, no es necesario ni recomendado para la mayoría de los escenarios. Tenga en cuenta que ninguna mejora significativa del rendimiento se logra mediante el uso de un tipo de datos es menor que <xref:System.Int32>. Si no puede usar el tipo de datos de forma predeterminada, debe usar uno de los sistema de Common Language (CLS)-compatible con tipos enteros, <xref:System.Byte>, <xref:System.Int16>, <xref:System.Int32>, o <xref:System.Int64> para asegurarse de que todos los valores de la enumeración se pueden representar en Lenguajes de programación conforme a CLS.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, a menos que existan problemas de compatibilidad o tamaño, utilice <xref:System.Int32>. Para las situaciones donde <xref:System.Int32> no es lo suficientemente grande como para contener los valores, use <xref:System.Int64>. Si la compatibilidad con versiones anteriores requiere un tipo de datos más pequeño, utilice <xref:System.Byte> o <xref:System.Int16>.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Suprima una advertencia de esta regla solo si lo requieren los problemas de compatibilidad con versiones anteriores. En las aplicaciones, incumplimiento de esta regla normalmente no provoca problemas. En bibliotecas, donde se requiere la interoperabilidad entre lenguajes, incumplimiento de esta regla puede afectar negativamente a los usuarios.

## <a name="example-of-a-violation"></a>Ejemplo de una infracción

### <a name="description"></a>Descripción
 El ejemplo siguiente muestra dos enumeraciones que no usan el tipo de datos subyacente recomendado.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Design.EnumIntegralType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralType/cs/FxCop.Design.EnumIntegralType.cs#1)]
 [!code-vb[FxCop.Design.EnumIntegralType#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralType/vb/FxCop.Design.EnumIntegralType.vb#1)]

## <a name="example-of-how-to-fix"></a>Ejemplo de cómo corregir

### <a name="description"></a>Descripción
 En el ejemplo siguiente se corrige la infracción anterior cambiando el tipo de datos subyacente <xref:System.Int32>.

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



