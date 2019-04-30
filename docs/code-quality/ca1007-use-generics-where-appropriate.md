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
ms.openlocfilehash: f1cf2939f0484c6defb76b88fb072fcd4b51849b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62779725"
---
# <a name="ca1007-use-generics-where-appropriate"></a>CA1007: Utilizar valores genéricos cuando sea posible

|||
|-|-|
|TypeName|UseGenericsWhereAppropriate|
|Identificador de comprobación|CA1007|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un método visible externamente contiene un parámetro de referencia de tipo <xref:System.Object?displayProperty=fullName>y los destinos de ensamblado que contiene [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)].

## <a name="rule-description"></a>Descripción de la regla
 Un parámetro de referencia es un parámetro que se modifica utilizando el `ref` (`ByRef` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) (palabra clave). El tipo de argumento proporcionado para un parámetro de referencia debe coincidir exactamente con el tipo de parámetro de referencia. Para usar un tipo que se deriva el tipo de parámetro de referencia, el tipo debe primero se convierte y asigna a una variable del tipo de parámetro de referencia. Uso de un método genérico permite a todos los tipos, sujeto a las restricciones, se pasa al método sin convertirlos antes al tipo al tipo de parámetro de referencia.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, hacer que el método genérico y reemplace el <xref:System.Object> parámetro mediante el uso de un parámetro de tipo.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra una rutina de intercambio de uso general que se implementa como métodos no genéricos y genéricos. Tenga en cuenta la eficacia con las cadenas se intercambian mediante el método genérico en comparación con el método no genérico.

 [!code-vb[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/VisualBasic/ca1007-use-generics-where-appropriate_1.vb)]
 [!code-csharp[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/CSharp/ca1007-use-generics-where-appropriate_1.cs)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1005: Evite parámetros excesivos en tipos genéricos](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Las colecciones deben implementar la interfaz genérica](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: No declarar a miembros estáticos en tipos genéricos](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: No exponer listas genéricas](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: No anidar tipos genéricos en firmas de miembro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Métodos genéricos deben proporcionar un parámetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Utilizar instancias de controlador de eventos genéricos](../code-quality/ca1003-use-generic-event-handler-instances.md)

## <a name="see-also"></a>Vea también
 [Genéricos](/dotnet/csharp/programming-guide/generics/index)