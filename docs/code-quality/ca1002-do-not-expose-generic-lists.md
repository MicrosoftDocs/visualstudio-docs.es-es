---
title: "CA1002: No exponer listas gen&#233;ricas | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotExposeGenericLists"
  - "CA1002"
helpviewer_keywords: 
  - "CA1002"
  - "DoNotExposeGenericLists"
ms.assetid: 5caac810-1a79-47df-a27b-c46c5040bf34
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1002: No exponer listas gen&#233;ricas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotExposeGenericLists|  
|Identificador de comprobación|CA1002|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un tipo contiene un miembro visible externamente que es un tipo <xref:System.Collections.Generic.List%601?displayProperty=fullName>, que devuelve un tipo <xref:System.Collections.Generic.List%601?displayProperty=fullName> o cuya firma incluye un parámetro <xref:System.Collections.Generic.List%601?displayProperty=fullName>.  
  
## Descripción de la regla  
 <xref:System.Collections.Generic.List%601?displayProperty=fullName> es una colección genérica que está diseñada para el rendimiento y no para la herencia.  <xref:System.Collections.Generic.List%601?displayProperty=fullName> no contiene miembros virtuales que facilitan el cambio de comportamiento de una clase heredada.  Las colecciones genéricas siguientes están diseñadas para herencia y se deberían exponer en lugar de <xref:System.Collections.Generic.List%601?displayProperty=fullName>.  
  
-   <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>  
  
-   <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>  
  
-   <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=fullName>  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, cambie el tipo <xref:System.Collections.Generic.List%601?displayProperty=fullName> por una de las colecciones genéricas diseñadas para la herencia.  
  
## Cuándo suprimir advertencias  
 No suprima ninguna advertencia de esta regla a menos que el ensamblado que la genera no se vaya a usar como biblioteca reutilizable.  Por ejemplo, sería seguro suprimir esta advertencia en una aplicación optimizada para el rendimiento cuando se obtenga una mejora importante del rendimiento usando listas genéricas.  
  
## Reglas relacionadas  
 [CA1005: Evite parámetros excesivos en tipos genéricos](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010: Las colecciones deben implementar la interfaz genérica](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000: No declarar miembros estáticos en tipos genéricos](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1006: No anidar tipos genéricos en firmas de miembro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004: Los métodos genéricos deben proporcionar un parámetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003: Utilizar instancias genéricas de controlador de eventos](../code-quality/ca1003-use-generic-event-handler-instances.md)  
  
 [CA1007: Utilizar valores genéricos cuando sea posible](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## Vea también  
 [Genéricos](/dotnet/csharp/programming-guide/generics/index)