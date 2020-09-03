---
title: 'CA1006: no anidar tipos genéricos en firmas de miembro | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotNestGenericTypesInMemberSignatures
- CA1006
helpviewer_keywords:
- CA1006
- DoNotNestGenericTypesInMemberSignatures
ms.assetid: dfc867bc-f4af-45d7-b071-db04a248f9fc
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 00992fc71f07d820620cecbe57eac4f3b3702701
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539651"
---
# <a name="ca1006-do-not-nest-generic-types-in-member-signatures"></a>CA1006: No anidar tipos genéricos en signaturas de miembro
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|DoNotNestGenericTypesInMemberSignatures|
|Identificador de comprobación|CA1006|
|Category|Microsoft. Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 Un miembro visible externamente tiene una firma que contiene un argumento de tipo anidado.

## <a name="rule-description"></a>Descripción de la regla
 Un argumento de tipo anidado es un argumento de tipo que también es un tipo genérico. Para llamar a un miembro cuya firma contenga un argumento de tipo anidado, el usuario debe crear instancias de un tipo genérico y pasar este tipo al constructor de un segundo tipo genérico. El procedimiento y la sintaxis necesarios para ello son complejos, por lo que es preferible evitarlo.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie el diseño para quitar el argumento de tipo anidado.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla. Proporcionar genéricos en una sintaxis que sea fácil de entender y usar reduce el tiempo necesario para aprender y aumentar la tasa de adopción de nuevas bibliotecas.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un método que infringe la regla y la sintaxis necesaria para llamar al método de infracción.

 [!code-csharp[FxCop.Design.NestedGenerics#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NestedGenerics/cs/FxCop.Design.NestedGenerics.cs#1)]
 [!code-vb[FxCop.Design.NestedGenerics#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NestedGenerics/vb/FxCop.Design.NestedGenerics.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1005: Evitar los parámetros excesivos en tipos genéricos](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Las colecciones deben implementar la interfaz genérica](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: No declarar miembros estáticos en tipos genéricos](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: No exponer listas genéricas](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1004: Los métodos genéricos deben proporcionar un parámetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Utilizar instancias genéricas de controlador de eventos](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: Utilizar valores genéricos cuando sea posible](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Consulte también
 [Genéricos](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
