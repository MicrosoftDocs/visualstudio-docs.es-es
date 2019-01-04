---
title: 'CA1003: Utilizar instancias genéricas de controlador de eventos'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- UseGenericEventHandlerInstances
- CA1003
helpviewer_keywords:
- CA1003
- UseGenericEventHandlerInstances
ms.assetid: 402101b6-555d-4cf7-b223-1d9fdfaaf1cd
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 26630aa008e944f0af3fdcc66a16dc4c08bd4e8b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53887340"
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003: Utilizar instancias genéricas de controlador de eventos

|||
|-|-|
|TypeName|UseGenericEventHandlerInstances|
|Identificador de comprobación|CA1003|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo contiene un delegado que devuelve void cuya firma contiene dos parámetros (el primero un objeto y el segundo un tipo asignable a EventArgs) y los destinos de ensamblado que contiene [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)].

## <a name="rule-description"></a>Descripción de la regla
 Antes de [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], para pasar información personalizada al controlador de eventos, era necesario declarar que especificó una clase que se derivó de un nuevo delegado el <xref:System.EventArgs?displayProperty=fullName> clase. Esto ya no es cierto en [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], que introdujo la <xref:System.EventHandler%601?displayProperty=fullName> delegar. Permite que cualquier clase que se deriva este delegado genérico <xref:System.EventArgs> para usarse junto con el controlador de eventos.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, quite el delegado y reemplace su uso con el <xref:System.EventHandler%601?displayProperty=fullName> delegar. Si el delegado es generado automáticamente por el [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] compilador, cambiar la sintaxis de la declaración de evento para usar el <xref:System.EventHandler%601?displayProperty=fullName> delegar.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra a un delegado que infringe la regla. En el [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ejemplo, los comentarios describen cómo modificar el ejemplo para cumplir la regla. Por ejemplo, C#, sigue un ejemplo que muestra el código modificado.

 [!code-vb[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/VisualBasic/ca1003-use-generic-event-handler-instances_1.vb)]
 [!code-csharp[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_1.cs)]

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se quita la declaración de delegado del ejemplo anterior, que cumple la regla y reemplaza su uso en el `ClassThatRaisesEvent` y `ClassThatHandlesEvent` métodos utilizando el <xref:System.EventHandler%601?displayProperty=fullName> delegar.

 [!code-csharp[FxCop.Design.GenericEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_2.cs)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1005: Evite parámetros excesivos en tipos genéricos](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Las colecciones deben implementar la interfaz genérica](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: No declarar a miembros estáticos en tipos genéricos](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: No exponer listas genéricas](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: No anidar tipos genéricos en firmas de miembro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Métodos genéricos deben proporcionar un parámetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1007: Utilizar valores genéricos cuando sea apropiado](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Vea también

- [Genéricos](/dotnet/csharp/programming-guide/generics/index)