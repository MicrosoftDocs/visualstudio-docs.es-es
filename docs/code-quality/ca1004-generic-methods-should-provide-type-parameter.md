---
title: 'CA1004: Los métodos genéricos deben proporcionar un parámetro de tipo'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1004
- GenericMethodsShouldProvideTypeParameter
helpviewer_keywords:
- GenericMethodsShouldProvideTypeParameter
- CA1004
ms.assetid: 38755f6a-fb45-4bf2-932e-0354ad826499
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 94c21a81a7473e1697609ff3e46eb054ad304540
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62779894"
---
# <a name="ca1004-generic-methods-should-provide-type-parameter"></a>CA1004: Los métodos genéricos deben proporcionar un parámetro de tipo

|||
|-|-|
|TypeName|GenericMethodsShouldProvideTypeParameter|
|Identificador de comprobación|CA1004|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 La firma de parámetro de un método genérico visible externamente no contiene tipos que corresponden a todos los parámetros de tipo del método.

## <a name="rule-description"></a>Descripción de la regla
 La inferencia es el modo en que se determina el argumento de tipo de un método genérico partiendo del tipo de argumento pasado al método, en lugar de especificar directamente el argumento de tipo. Para habilitar la inferencia, la firma de parámetro de un método genérico debe incluir un parámetro del mismo tipo que el parámetro type del método. En este caso, no es necesario especificar el argumento de tipo. Al utilizar la inferencia para todos los parámetros de tipo, la sintaxis para llamar a métodos de instancia genéricos y es idéntica. Esto simplifica el uso de métodos genéricos.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie el diseño para que la firma del parámetro contiene el mismo tipo para cada parámetro de tipo del método.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 No suprima las advertencias de esta regla. Al proporcionar genéricos con una sintaxis fácil de entender y usar reduce el tiempo necesario para obtener información y aumenta la tasa de adopción de nuevas bibliotecas.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra la sintaxis para llamar a dos métodos genéricos. El argumento de tipo para `InferredTypeArgument` se deduce y el argumento de tipo para `NotInferredTypeArgument` debe especificarse explícitamente.

 [!code-vb[FxCop.Design.Inference#1](../code-quality/codesnippet/VisualBasic/ca1004-generic-methods-should-provide-type-parameter_1.vb)]
 [!code-csharp[FxCop.Design.Inference#1](../code-quality/codesnippet/CSharp/ca1004-generic-methods-should-provide-type-parameter_1.cs)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1005: Evite parámetros excesivos en tipos genéricos](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Las colecciones deben implementar la interfaz genérica](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: No declarar a miembros estáticos en tipos genéricos](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: No exponer listas genéricas](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: No anidar tipos genéricos en firmas de miembro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1003: Utilizar instancias de controlador de eventos genéricos](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: Utilizar valores genéricos cuando sea apropiado](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Vea también
 [Genéricos](/dotnet/csharp/programming-guide/generics/index)