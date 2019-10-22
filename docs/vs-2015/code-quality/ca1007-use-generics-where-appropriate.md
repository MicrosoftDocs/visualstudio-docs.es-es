---
title: 'CA1007: Use genéricos cuando corresponda | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1007
- UseGenericsWhereAppropriate
helpviewer_keywords:
- CA1007
- UseGenericsWhereAppropriate
ms.assetid: eab780ea-3b1f-4d32-b15a-5d48da2df46b
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 22c9bac17a957438ee8d2a6f4b634f30604ed1ff
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668957"
---
# <a name="ca1007-use-generics-where-appropriate"></a>CA1007: Utilizar valores genéricos cuando sea posible
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseGenericsWhereAppropriate|
|Identificador de comprobación|CA1007|
|Categoría|Microsoft. Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un método visible externamente contiene un parámetro de referencia de tipo <xref:System.Object?displayProperty=fullName>, y el ensamblado contenedor tiene como destino [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)].

## <a name="rule-description"></a>Descripción de la regla
 Un parámetro de referencia es un parámetro que se modifica mediante la palabra clave `ref` (`ByRef` en [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]). El tipo de argumento que se proporciona para un parámetro de referencia debe coincidir exactamente con el tipo de parámetro de referencia. Para usar un tipo que se deriva del tipo de parámetro de referencia, primero se debe convertir el tipo y asignarlo a una variable del tipo de parámetro de referencia. El uso de un método genérico permite que todos los tipos, sujetos a restricciones, se pasen al método sin convertir primero el tipo al tipo de parámetro de referencia.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, haga que el método sea genérico y reemplace el parámetro <xref:System.Object> mediante un parámetro de tipo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra una rutina de intercambio de uso general que se implementa como métodos genéricos y no genéricos. Observe la eficacia con la que se intercambian las cadenas mediante el método genérico en comparación con el método no genérico.

 [!code-csharp[FxCop.Design.UseGenerics#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UseGenerics/cs/FxCop.Design.UseGenerics.cs#1)]
 [!code-vb[FxCop.Design.UseGenerics#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UseGenerics/vb/FxCop.Design.UseGenerics.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1005: Evite parámetros excesivos en tipos genéricos](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Las colecciones deben implementar la interfaz genérica](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: No declarar miembros estáticos en tipos genéricos](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: No exponer listas genéricas](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: No anidar tipos genéricos en firmas de miembro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Los métodos genéricos deben proporcionar un parámetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Utilizar instancias genéricas de controlador de eventos](../code-quality/ca1003-use-generic-event-handler-instances.md)

## <a name="see-also"></a>Vea también
 [Genéricos](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
