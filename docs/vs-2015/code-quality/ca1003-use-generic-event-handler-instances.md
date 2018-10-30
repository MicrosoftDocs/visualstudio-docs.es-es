---
title: 'CA1003: Utilizar instancias de controlador de eventos genéricos | Microsoft Docs'
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
- UseGenericEventHandlerInstances
- CA1003
helpviewer_keywords:
- CA1003
- UseGenericEventHandlerInstances
ms.assetid: 402101b6-555d-4cf7-b223-1d9fdfaaf1cd
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f3c2cf2ad59f7ade337c84f13133bb5181afb615
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49929093"
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003: Utilizar instancias genéricas de controlador de eventos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseGenericEventHandlerInstances|
|Identificador de comprobación|CA1003|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo contiene un delegado que devuelve void cuya firma contiene dos parámetros (el primero un objeto y el segundo un tipo asignable a EventArgs) y los destinos de ensamblado que contiene [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)].

## <a name="rule-description"></a>Descripción de la regla
 Antes de [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)], para pasar información personalizada al controlador de eventos, era necesario declarar que especificó una clase que se derivó de un nuevo delegado el <xref:System.EventArgs?displayProperty=fullName> clase. Esto ya no es cierto en [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)], que introdujo la <xref:System.EventHandler%601?displayProperty=fullName> delegar. Permite que cualquier clase que se deriva este delegado genérico <xref:System.EventArgs> para usarse junto con el controlador de eventos.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, quite el delegado y reemplace su uso con el <xref:System.EventHandler%601?displayProperty=fullName> delegar. Si el delegado es generado automáticamente por el [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] compilador, cambiar la sintaxis de la declaración de evento para usar el <xref:System.EventHandler%601?displayProperty=fullName> delegar.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra a un delegado que infringe la regla. En el [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ejemplo, los comentarios describen cómo modificar el ejemplo para cumplir la regla. Por ejemplo, C#, sigue un ejemplo que muestra el código modificado.

 [!code-csharp[FxCop.Design.CustomEventHandler#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CustomEventHandler/cs/FxCop.Design.CustomEventHandler.cs#1)]
 [!code-vb[FxCop.Design.CustomEventHandler#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.CustomEventHandler/vb/FxCop.Design.CustomEventHandler.vb#1)]

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se quita la declaración de delegado del ejemplo anterior, que cumple la regla y reemplaza su uso en el `ClassThatRaisesEvent` y `ClassThatHandlesEvent` métodos utilizando el <xref:System.EventHandler%601?displayProperty=fullName> delegar.

 [!code-csharp[FxCop.Design.GenericEventHandler#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.GenericEventHandler/cs/FxCop.Design.GenericEventHandler.cs#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1005: Evite parámetros excesivos en tipos genéricos](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Las colecciones deben implementar la interfaz genérica](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: No declarar miembros estáticos en tipos genéricos](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: No exponer listas genéricas](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: No anidar tipos genéricos en firmas de miembro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Los métodos genéricos deben proporcionar un parámetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1007: Utilizar valores genéricos cuando sea posible](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Vea también
 [Genéricos](http://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)



