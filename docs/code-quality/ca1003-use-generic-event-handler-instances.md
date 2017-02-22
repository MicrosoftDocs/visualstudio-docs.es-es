---
title: "CA1003: Utilizar instancias gen&#233;ricas de controlador de eventos | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UseGenericEventHandlerInstances"
  - "CA1003"
helpviewer_keywords: 
  - "CA1003"
  - "UseGenericEventHandlerInstances"
ms.assetid: 402101b6-555d-4cf7-b223-1d9fdfaaf1cd
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1003: Utilizar instancias gen&#233;ricas de controlador de eventos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseGenericEventHandlerInstances|  
|Identificador de comprobación|CA1003|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un tipo contiene un delegado que devuelve void cuya firma contiene dos parámetros \(el primero un objeto y el segundo un tipo asignable a EventArgs\), y el ensamblado que lo contiene está dirigido a [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)].  
  
## Descripción de la regla  
 Antes de [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], para poder pasar información personalizada al controlador de eventos, era necesario declarar un nuevo delegado que especificaba una clase que derivaba de la clase <xref:System.EventArgs?displayProperty=fullName>.  Esto ya no es necesario en [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], con la introducción del delegado <xref:System.EventHandler%601?displayProperty=fullName>.  Este delegado genérico permite que cualquier clase derivada de <xref:System.EventArgs> se utilice junto con el controlador de eventos.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, quite el delegado y reemplace su uso utilizando el delegado <xref:System.EventHandler%601?displayProperty=fullName>.  Si el compilador de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] genera automáticamente el delegado, cambie la sintaxis de la declaración de evento para utilizar el delegado de <xref:System.EventHandler%601?displayProperty=fullName>.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo  
 El siguiente ejemplo muestra un delegado que infringe la regla.  En el ejemplo de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], los comentarios describen cómo modificar el ejemplo de modo que se cumpla la regla.  En cuanto al ejemplo de C\#, a continuación figura un ejemplo que muestra el código modificado.  
  
 [!code-vb[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/VisualBasic/ca1003-use-generic-event-handler-instances_1.vb)]
 [!code-cs[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_1.cs)]  
  
## Ejemplo  
 El ejemplo siguiente quita la declaración de delegado del ejemplo anterior, que cumple la regla, y reemplaza su uso en los métodos `ClassThatRaisesEvent` y `ClassThatHandlesEvent` mediante el delegado <xref:System.EventHandler%601?displayProperty=fullName>.  
  
 [!code-cs[FxCop.Design.GenericEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_2.cs)]  
  
## Reglas relacionadas  
 [CA1005: Evite parámetros excesivos en tipos genéricos](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010: Las colecciones deben implementar la interfaz genérica](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000: No declarar miembros estáticos en tipos genéricos](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: No exponer listas genéricas](../code-quality/ca1002-do-not-expose-generic-lists.md)  
  
 [CA1006: No anidar tipos genéricos en firmas de miembro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004: Los métodos genéricos deben proporcionar un parámetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1007: Utilizar valores genéricos cuando sea posible](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## Vea también  
 [Genéricos](/dotnet/csharp/programming-guide/generics/index)