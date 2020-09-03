---
title: 'CA1003: usar instancias de controlador de eventos genéricos | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseGenericEventHandlerInstances
- CA1003
helpviewer_keywords:
- CA1003
- UseGenericEventHandlerInstances
ms.assetid: 402101b6-555d-4cf7-b223-1d9fdfaaf1cd
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ee0571e85a1d4ec9960e0235814fcb9d7adbd483
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539911"
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003: Utilizar instancias genéricas de controlador de eventos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|UseGenericEventHandlerInstances|
|Identificador de comprobación|CA1003|
|Category|Microsoft. Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 Un tipo contiene un delegado que devuelve void, cuya firma contiene dos parámetros (el primero es un objeto y el segundo un tipo que se puede asignar a EventArgs) y el ensamblado que contiene destinos [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] .

## <a name="rule-description"></a>Descripción de la regla
 Antes [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] de, para pasar información personalizada al controlador de eventos, había que declarar un nuevo delegado que especifica una clase que se deriva de la <xref:System.EventArgs?displayProperty=fullName> clase. Esto ya no es así en [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] , que presentó el <xref:System.EventHandler%601?displayProperty=fullName> delegado. Este delegado genérico permite que cualquier clase derivada de <xref:System.EventArgs> se use junto con el controlador de eventos.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, quite el delegado y reemplace su uso con el <xref:System.EventHandler%601?displayProperty=fullName> delegado. Si el compilador genera automáticamente el delegado [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] , cambie la sintaxis de la declaración de evento para usar el <xref:System.EventHandler%601?displayProperty=fullName> delegado.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un delegado que infringe la regla. En el [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ejemplo, los comentarios describen cómo modificar el ejemplo para satisfacer la regla. En el ejemplo de C#, se muestra un ejemplo que muestra el código modificado.

 [!code-csharp[FxCop.Design.CustomEventHandler#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CustomEventHandler/cs/FxCop.Design.CustomEventHandler.cs#1)]
 [!code-vb[FxCop.Design.CustomEventHandler#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.CustomEventHandler/vb/FxCop.Design.CustomEventHandler.vb#1)]

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se quita la declaración de delegado del ejemplo anterior, que cumple la regla, y se reemplaza su uso en los `ClassThatRaisesEvent` métodos y mediante `ClassThatHandlesEvent` el <xref:System.EventHandler%601?displayProperty=fullName> delegado.

 [!code-csharp[FxCop.Design.GenericEventHandler#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.GenericEventHandler/cs/FxCop.Design.GenericEventHandler.cs#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1005: Evitar los parámetros excesivos en tipos genéricos](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Las colecciones deben implementar la interfaz genérica](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: No declarar miembros estáticos en tipos genéricos](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: No exponer listas genéricas](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: No anidar tipos genéricos en signaturas de miembro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Los métodos genéricos deben proporcionar un parámetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1007: Utilizar valores genéricos cuando sea posible](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Consulte también
 [Genéricos](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
