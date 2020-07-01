---
title: 'CA1008: las enumeraciones deben tener un valor cero | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1008
- EnumsShouldHaveZeroValue
helpviewer_keywords:
- CA1008
- EnumsShouldHaveZeroValue
ms.assetid: 3503a73c-360c-416d-8ee4-c2aa44365a05
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0ca58938a55330243315529e9c7990b59d1a6fe5
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548348"
---
# <a name="ca1008-enums-should-have-zero-value"></a>CA1008: Las enumeraciones deben tener un valor igual a cero
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|EnumsShouldHaveZeroValue|
|Identificador de comprobación|CA1008|
|Category|Microsoft. Design|
|Cambio problemático|Sin interrupciones: cuando se le pide que agregue un valor **None** a una enumeración sin marca. Interrumpir: cuando se le pida que cambie el nombre o quite los valores de enumeración.|

## <a name="cause"></a>Causa
 Una enumeración sin un <xref:System.FlagsAttribute?displayProperty=fullName> elemento aplicado no define un miembro que tiene un valor de cero; o una enumeración que tiene un aplicado <xref:System.FlagsAttribute> define un miembro que tiene un valor de cero pero su nombre no es ' none ', o la enumeración define varios miembros con valores cero.

## <a name="rule-description"></a>Descripción de la regla
 El valor predeterminado de una enumeración no inicializada, al igual que otros tipos de valor, es cero. Una enumeración que no sea de marcas debe definir un miembro que tenga el valor de cero para que el valor predeterminado sea un valor válido de la enumeración. Si es necesario, asigne al miembro el nombre ' none '. De lo contrario, asigne cero al miembro usado con más frecuencia. Tenga en cuenta que, de forma predeterminada, si el valor del primer miembro de la enumeración no se establece en la declaración, su valor es cero.

 Si una enumeración que tiene <xref:System.FlagsAttribute> aplicado define un miembro con valor cero, su nombre debe ser ' none ' para indicar que no se ha establecido ningún valor en la enumeración. El uso de un miembro con valor cero para cualquier otro propósito es contrario al uso de <xref:System.FlagsAttribute> en que los operadores bit a and y or no son útiles con el miembro. Esto implica que solo un miembro debe tener asignado el valor cero. Tenga en cuenta que si se producen varios miembros que tienen el valor cero en una enumeración con atributos de marcas, `Enum.ToString()` devuelve resultados incorrectos para los miembros que no son cero.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla en las enumeraciones con atributos que no son de marcas, defina un miembro que tenga el valor de cero; se trata de un cambio no problemático. En el caso de las enumeraciones con atributos de marcas que definen un miembro con valor cero, asigne un nombre a este miembro ' none ' y elimine cualquier otro miembro que tenga un valor de cero; se trata de un cambio importante.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima una advertencia de esta regla excepto para las enumeraciones con atributos de marcas que se hayan enviado previamente.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestran dos enumeraciones que cumplen la regla y una enumeración, `BadTraceOptions` , que infringe la regla.

 [!code-cpp[FxCop.Design.EnumsZeroValue#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/cpp/FxCop.Design.EnumsZeroValue.cpp#1)]
 [!code-csharp[FxCop.Design.EnumsZeroValue#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/cs/FxCop.Design.EnumsZeroValue.cs#1)]
 [!code-vb[FxCop.Design.EnumsZeroValue#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/vb/FxCop.Design.EnumsZeroValue.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA2217: No marcar enumeraciones con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1700: No nombrar valores de enumeración como 'Reserved'](../code-quality/ca1700-do-not-name-enum-values-reserved.md)

 [CA1712: No utilizar prefijos en valores de enumeración con el nombre del tipo](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

 [CA1028: El almacenamiento de la enumeración debe ser de tipo Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)

 [CA1027: Marcar enumeraciones con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Consulte también
 <xref:System.Enum?displayProperty=fullName>
