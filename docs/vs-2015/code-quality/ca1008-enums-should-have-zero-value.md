---
title: 'CA1008: Las enumeraciones deben tener un valor cero | Microsoft Docs'
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
- CA1008
- EnumsShouldHaveZeroValue
helpviewer_keywords:
- CA1008
- EnumsShouldHaveZeroValue
ms.assetid: 3503a73c-360c-416d-8ee4-c2aa44365a05
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 69e60b0f2ee8106b04507722f1b3094e1bbdbbc8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49874831"
---
# <a name="ca1008-enums-should-have-zero-value"></a>CA1008: Las enumeraciones deben tener un valor igual a cero
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|EnumsShouldHaveZeroValue|
|Identificador de comprobación|CA1008|
|Categoría|Microsoft.Design|
|Cambio problemático|No problemático: cuando se le pida que agregue un **ninguno** valor a una enumeración sin marca. Problemático: cuando se le pedirá que cambie el nombre o quitar cualquier valor de enumeración.|

## <a name="cause"></a>Motivo
 Una enumeración sin un aplicada <xref:System.FlagsAttribute?displayProperty=fullName> no define un miembro que tiene un valor de cero; o una enumeración que tiene un aplicada <xref:System.FlagsAttribute> define un miembro que tiene un valor de cero, pero su nombre no es 'None' o la enumeración define varios con valor cero miembros.

## <a name="rule-description"></a>Descripción de la regla
 El valor predeterminado de una enumeración no inicializada, igual que otros tipos de valor, es cero. Una enumeración no flags−attributed debe definir a un miembro que tiene el valor de cero para que el valor predeterminado es un valor válido de la enumeración. Si es necesario, el nombre del miembro 'None'. De lo contrario, asigna el valor cero para el miembro que se usan con más frecuencia. Tenga en cuenta que, de forma predeterminada, si el valor del primer miembro de enumeración no se establece en la declaración, su valor es cero.

 Si una enumeración que tiene el <xref:System.FlagsAttribute> aplicado define un miembro con valor cero, su nombre debe ser 'None' para indicar que no se ha establecido ningún valor en la enumeración. Uso de un miembro con valor cero para cualquier otro propósito es contrario a la utilización de la <xref:System.FlagsAttribute> en que la operación AND y o los operadores bit a bit son útiles con el miembro. Esto implica que solo un miembro debe tener asignado el valor cero. Tenga en cuenta que si varios miembros que tienen el valor cero se produce en una enumeración con atributos de marcas, `Enum.ToString()` devuelve resultados incorrectos para los miembros que no son cero.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla para las enumeraciones no flags−attributed, definir a un miembro que tiene el valor de cero; se trata de un cambio sin interrupción. Para las enumeraciones con atributos de marcas que definen a un miembro con valor cero, denomine al miembro 'None' y eliminar a todos los miembros que tienen un valor de cero; se trata de un cambio importante.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima una advertencia de esta regla excepto para atribuyen en indicadores enumeraciones que anteriormente se han enviado.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra dos enumeraciones que cumplen la regla y una enumeración, `BadTraceOptions`, que infringe la regla.

 [!code-cpp[FxCop.Design.EnumsZeroValue#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/cpp/FxCop.Design.EnumsZeroValue.cpp#1)]
 [!code-csharp[FxCop.Design.EnumsZeroValue#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/cs/FxCop.Design.EnumsZeroValue.cs#1)]
 [!code-vb[FxCop.Design.EnumsZeroValue#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/vb/FxCop.Design.EnumsZeroValue.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA2217: No marcar enumeraciones con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1700: No nombrar valores de enumeración como 'Reserved'](../code-quality/ca1700-do-not-name-enum-values-reserved.md)

 [CA1712: No utilizar prefijos en valores de enumeración con el nombre del tipo](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

 [CA1028: El almacenamiento de la enumeración debe ser de tipo Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)

 [CA1027: Marcar enumeraciones con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Vea también
 <xref:System.Enum?displayProperty=fullName>



