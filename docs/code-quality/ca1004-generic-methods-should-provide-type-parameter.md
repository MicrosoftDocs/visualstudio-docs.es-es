---
title: "CA1004: Los métodos genéricos deben proporcionar un parámetro de tipo | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1004
- GenericMethodsShouldProvideTypeParameter
helpviewer_keywords:
- GenericMethodsShouldProvideTypeParameter
- CA1004
ms.assetid: 38755f6a-fb45-4bf2-932e-0354ad826499
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4ca506d827c954a9863a6a37efd0980ecf4d8452
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="ca1004-generic-methods-should-provide-type-parameter"></a>CA1004: Los métodos genéricos deben proporcionar un parámetro de tipo
|||  
|-|-|  
|TypeName|GenericMethodsShouldProvideTypeParameter|  
|Identificador de comprobación|CA1004|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 La firma del parámetro de un método genérico visible externamente no contiene tipos que corresponden a todos los parámetros de tipo del método.  
  
## <a name="rule-description"></a>Descripción de la regla  
 La inferencia es el modo en que se determina el argumento de tipo de un método genérico partiendo del tipo de argumento pasado al método, en lugar de especificar directamente el argumento de tipo. Para habilitar la inferencia, la firma de parámetro de un método genérico debe incluir un parámetro del mismo tipo que el parámetro type del método. En este caso, no es necesario especificar el argumento de tipo. Al utilizar la inferencia para todos los parámetros de tipo, la sintaxis para llamar a métodos de instancia genéricos y no genéricos es idéntica. Esto simplifica la facilidad de uso de los métodos genéricos.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, cambie el diseño para que la firma del parámetro contiene el mismo tipo para cada parámetro de tipo del método.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla. Al proporcionar genéricos con una sintaxis que sea fácil de entender y usar reduce el tiempo que se necesita para obtener información y aumenta la velocidad de adopción de nuevas bibliotecas.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra la sintaxis para llamar a dos métodos genéricos. El argumento de tipo para `InferredTypeArgument` se deduce y el argumento de tipo para `NotInferredTypeArgument` debe especificarse explícitamente.  
  
 [!code-vb[FxCop.Design.Inference#1](../code-quality/codesnippet/VisualBasic/ca1004-generic-methods-should-provide-type-parameter_1.vb)]
 [!code-csharp[FxCop.Design.Inference#1](../code-quality/codesnippet/CSharp/ca1004-generic-methods-should-provide-type-parameter_1.cs)]  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [CA1005: Evite parámetros excesivos en tipos genéricos](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010: Las colecciones deben implementar la interfaz genérica](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000: No declarar miembros estáticos en tipos genéricos](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: No exponer listas genéricas](../code-quality/ca1002-do-not-expose-generic-lists.md)  
  
 [CA1006: No anidar tipos genéricos en firmas de miembro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1003: Utilizar instancias genéricas de controlador de eventos](../code-quality/ca1003-use-generic-event-handler-instances.md)  
  
 [CA1007: Utilizar valores genéricos cuando sea posible](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## <a name="see-also"></a>Vea también  
 [Genéricos](/dotnet/csharp/programming-guide/generics/index)