---
title: 'CA1007: Utilizar valores genéricos cuando sea posible'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6379a811da7c62be59a322ee68ad9f030d9693d9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31899722"
---
# <a name="ca1007-use-generics-where-appropriate"></a>CA1007: Utilizar valores genéricos cuando sea posible
|||
|-|-|
|TypeName|UseGenericsWhereAppropriate|
|Identificador de comprobación|CA1007|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un método visible externamente contiene un parámetro de referencia de tipo <xref:System.Object?displayProperty=fullName>y los destinos de ensamblado que lo contiene [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)].

## <a name="rule-description"></a>Descripción de la regla
 Un parámetro de referencia es un parámetro que se modifica utilizando la `ref` (`ByRef` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) (palabra clave). El tipo de argumento que se proporciona para un parámetro de referencia debe coincidir exactamente con el tipo de parámetro de referencia. Para utilizar un tipo que se deriva el tipo de parámetro de referencia, el tipo debe en primer lugar se convierte y asigna a una variable del tipo de parámetro de referencia. Uso de un método genérico permite a todos los tipos, sujeto a las restricciones, que se pasa al método sin convertirlos antes al tipo para el tipo de parámetro de referencia.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, haga que el método genérico y reemplace el <xref:System.Object> parámetro mediante el uso de un parámetro de tipo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra una rutina de intercambio de uso general que se implementa como métodos genéricos y no genéricos. Tenga en cuenta la eficiencia con las cadenas se intercambian mediante el método genérico en comparación con el método no genérico.

 [!code-vb[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/VisualBasic/ca1007-use-generics-where-appropriate_1.vb)]
 [!code-csharp[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/CSharp/ca1007-use-generics-where-appropriate_1.cs)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1005: Evite parámetros excesivos en tipos genéricos](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Las colecciones deben implementar la interfaz genérica](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: No declarar miembros estáticos en tipos genéricos](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: No exponer listas genéricas](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: No anidar tipos genéricos en firmas de miembro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Los métodos genéricos deben proporcionar un parámetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Utilizar instancias genéricas de controlador de eventos](../code-quality/ca1003-use-generic-event-handler-instances.md)

## <a name="see-also"></a>Vea también
 [Genéricos](/dotnet/csharp/programming-guide/generics/index)