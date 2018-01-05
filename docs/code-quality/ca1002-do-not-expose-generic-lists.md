---
title: "CA1002: No exponer listas genéricas | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotExposeGenericLists
- CA1002
helpviewer_keywords:
- CA1002
- DoNotExposeGenericLists
ms.assetid: 5caac810-1a79-47df-a27b-c46c5040bf34
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d98b088b663eca89b04ea264a582a062d324a473
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="ca1002-do-not-expose-generic-lists"></a>CA1002: No exponer listas genéricas
|||  
|-|-|  
|TypeName|DoNotExposeGenericLists|  
|Identificador de comprobación|CA1002|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 Un tipo contiene un miembro visible externamente que es un <xref:System.Collections.Generic.List%601?displayProperty=fullName> escribe, devuelve un <xref:System.Collections.Generic.List%601?displayProperty=fullName> tipo o cuya firma incluye un <xref:System.Collections.Generic.List%601?displayProperty=fullName> parámetro.  
  
## <a name="rule-description"></a>Descripción de la regla  
 <xref:System.Collections.Generic.List%601?displayProperty=fullName>es una colección genérica diseñada para el rendimiento y no para la herencia. <xref:System.Collections.Generic.List%601?displayProperty=fullName>no contiene a miembros virtuales que resulten más fácil cambiar el comportamiento de una clase heredada. Las siguientes colecciones genéricas diseñadas para herencia y deben exponerse en lugar de <xref:System.Collections.Generic.List%601?displayProperty=fullName>.  
  
-   <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>  
  
-   <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>  
  
-   <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=fullName>  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, cambie el <xref:System.Collections.Generic.List%601?displayProperty=fullName> tipo a una de las colecciones genéricas diseñadas para herencia.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla a menos que el ensamblado que genera esta advertencia no pretende ser una biblioteca reutilizable. Por ejemplo, sería seguro suprimir esta advertencia en una aplicación ajustada para el rendimiento que se ha obtenido una mejora del rendimiento del uso de listas genéricas.  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [CA1005: Evite parámetros excesivos en tipos genéricos](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010: Las colecciones deben implementar la interfaz genérica](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000: No declarar miembros estáticos en tipos genéricos](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1006: No anidar tipos genéricos en firmas de miembro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004: Los métodos genéricos deben proporcionar un parámetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003: Utilizar instancias genéricas de controlador de eventos](../code-quality/ca1003-use-generic-event-handler-instances.md)  
  
 [CA1007: Utilizar valores genéricos cuando sea posible](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## <a name="see-also"></a>Vea también  
 [Genéricos](/dotnet/csharp/programming-guide/generics/index)