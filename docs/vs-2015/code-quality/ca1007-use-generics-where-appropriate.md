---
title: 'CA1007: Utilizar valores genéricos | Documentos de Microsoft'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2d4f5f7749ad34f62e9dfa5718c6a778d6e7bebf
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704292"
---
# <a name="ca1007-use-generics-where-appropriate"></a>CA1007: Utilizar valores genéricos cuando sea posible
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseGenericsWhereAppropriate|
|Identificador de comprobación|CA1007|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un método visible externamente contiene un parámetro de referencia de tipo <xref:System.Object?displayProperty=fullName>y los destinos de ensamblado que contiene [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)].

## <a name="rule-description"></a>Descripción de la regla
 Un parámetro de referencia es un parámetro que se modifica utilizando el `ref` (`ByRef` en [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) (palabra clave). El tipo de argumento proporcionado para un parámetro de referencia debe coincidir exactamente con el tipo de parámetro de referencia. Para usar un tipo que se deriva el tipo de parámetro de referencia, el tipo debe primero se convierte y asigna a una variable del tipo de parámetro de referencia. Uso de un método genérico permite a todos los tipos, sujeto a las restricciones, se pasa al método sin convertirlos antes al tipo al tipo de parámetro de referencia.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, hacer que el método genérico y reemplace el <xref:System.Object> parámetro mediante el uso de un parámetro de tipo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra una rutina de intercambio de uso general que se implementa como métodos no genéricos y genéricos. Tenga en cuenta la eficacia con las cadenas se intercambian mediante el método genérico en comparación con el método no genérico.

 [!code-csharp[FxCop.Design.UseGenerics#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UseGenerics/cs/FxCop.Design.UseGenerics.cs#1)]
 [!code-vb[FxCop.Design.UseGenerics#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UseGenerics/vb/FxCop.Design.UseGenerics.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1005: Evite parámetros excesivos en tipos genéricos](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Las colecciones deben implementar la interfaz genérica](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: No declarar a miembros estáticos en tipos genéricos](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: No exponer listas genéricas](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: No anidar tipos genéricos en firmas de miembro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Métodos genéricos deben proporcionar un parámetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Utilizar instancias de controlador de eventos genéricos](../code-quality/ca1003-use-generic-event-handler-instances.md)

## <a name="see-also"></a>Vea también
 [Genéricos](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
