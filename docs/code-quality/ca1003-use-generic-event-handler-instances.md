---
title: "CA1003: Utilizar instancias de controlador de eventos genéricos | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UseGenericEventHandlerInstances
- CA1003
helpviewer_keywords:
- CA1003
- UseGenericEventHandlerInstances
ms.assetid: 402101b6-555d-4cf7-b223-1d9fdfaaf1cd
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 66f18e0b62d5dc2526d97109949c0dda21ad4e71
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003: Utilizar instancias genéricas de controlador de eventos
|||  
|-|-|  
|TypeName|UseGenericEventHandlerInstances|  
|Identificador de comprobación|CA1003|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 Un tipo contiene un delegado que devuelve void cuya firma contiene dos parámetros (el primero un objeto y el segundo un tipo asignable a EventArgs) y los destinos de ensamblado que lo contiene [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)].  
  
## <a name="rule-description"></a>Descripción de la regla  
 Antes de [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], con el fin de pasar información personalizada al controlador de eventos, era un nuevo delegado que se declaren que especificó una clase que se deriva de la <xref:System.EventArgs?displayProperty=fullName> clase. Esto ya no es así en [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], que introdujo la <xref:System.EventHandler%601?displayProperty=fullName> delegar. Este delegado genérico permite que cualquier clase que se deriva de <xref:System.EventArgs> para usarse junto con el controlador de eventos.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, quite el delegado y reemplazar su uso con el <xref:System.EventHandler%601?displayProperty=fullName> delegar. Si el delegado es generado automáticamente por el [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] compilador, cambie la sintaxis de la declaración de evento para usar el <xref:System.EventHandler%601?displayProperty=fullName> delegar.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra a un delegado que infringe la regla. En la [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ejemplo, los comentarios describen cómo modificar el ejemplo para cumplir la regla. Por ejemplo, C#, continuación encontrará un ejemplo que muestra el código modificado.  
  
 [!code-vb[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/VisualBasic/ca1003-use-generic-event-handler-instances_1.vb)]
 [!code-csharp[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_1.cs)]  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se quita la declaración de delegado del ejemplo anterior, que cumple la regla y reemplaza su uso en el `ClassThatRaisesEvent` y `ClassThatHandlesEvent` métodos mediante el uso de la <xref:System.EventHandler%601?displayProperty=fullName> delegar.  
  
 [!code-csharp[FxCop.Design.GenericEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_2.cs)]  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [CA1005: Evite parámetros excesivos en tipos genéricos](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010: Las colecciones deben implementar la interfaz genérica](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000: No declarar miembros estáticos en tipos genéricos](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: No exponer listas genéricas](../code-quality/ca1002-do-not-expose-generic-lists.md)  
  
 [CA1006: No anidar tipos genéricos en firmas de miembro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004: Los métodos genéricos deben proporcionar un parámetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1007: Utilizar valores genéricos cuando sea posible](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## <a name="see-also"></a>Vea también  
 [Genéricos](/dotnet/csharp/programming-guide/generics/index)