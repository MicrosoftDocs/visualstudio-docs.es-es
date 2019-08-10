---
title: 'CA1007: Utilizar valores genéricos cuando sea posible'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1007
- UseGenericsWhereAppropriate
helpviewer_keywords:
- CA1007
- UseGenericsWhereAppropriate
ms.assetid: eab780ea-3b1f-4d32-b15a-5d48da2df46b
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: ffb18316b5f009a0f2854c8a158e528f15c92326
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923206"
---
# <a name="ca1007-use-generics-where-appropriate"></a>CA1007: Utilizar valores genéricos cuando sea posible

|||
|-|-|
|TypeName|UseGenericsWhereAppropriate|
|Identificador de comprobación|CA1007|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
Un método visible externamente contiene un parámetro de referencia de <xref:System.Object?displayProperty=fullName>tipo y el ensamblado contenedor tiene como destino .NET Framework 2,0.

## <a name="rule-description"></a>Descripción de la regla
Un parámetro de referencia es un parámetro que se modifica mediante la `ref` palabra`ByRef` clave [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)](en). El tipo de argumento que se proporciona para un parámetro de referencia debe coincidir exactamente con el tipo de parámetro de referencia. Para usar un tipo que se deriva del tipo de parámetro de referencia, primero se debe convertir el tipo y asignarlo a una variable del tipo de parámetro de referencia. El uso de un método genérico permite que todos los tipos, sujetos a restricciones, se pasen al método sin convertir primero el tipo al tipo de parámetro de referencia.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, haga que el método sea genérico <xref:System.Object> y reemplace el parámetro mediante un parámetro de tipo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra una rutina de intercambio de uso general que se implementa como métodos genéricos y no genéricos. Observe la eficacia con la que se intercambian las cadenas mediante el método genérico en comparación con el método no genérico.

[!code-vb[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/VisualBasic/ca1007-use-generics-where-appropriate_1.vb)]
[!code-csharp[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/CSharp/ca1007-use-generics-where-appropriate_1.cs)]

## <a name="related-rules"></a>Reglas relacionadas
[CA1005: Evite parámetros excesivos en tipos genéricos](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

[CA1010: Las colecciones deben implementar la interfaz genérica](../code-quality/ca1010-collections-should-implement-generic-interface.md)

[CA1000: No declarar miembros estáticos en tipos genéricos](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

[CA1002: No exponer listas genéricas](../code-quality/ca1002-do-not-expose-generic-lists.md)

[CA1006: No anide tipos genéricos en firmas de miembro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

[CA1004: Los métodos genéricos deben proporcionar un parámetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

[CA1003: Usar instancias de controlador de eventos genéricos](../code-quality/ca1003-use-generic-event-handler-instances.md)

## <a name="see-also"></a>Vea también
[Genéricos](/dotnet/csharp/programming-guide/generics/index)