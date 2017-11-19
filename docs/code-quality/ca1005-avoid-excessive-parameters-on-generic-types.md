---
title: "CA1005: Evite parámetros excesivos en tipos genéricos | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidExcessiveParametersOnGenericTypes
- CA1005
helpviewer_keywords:
- AvoidExcessiveParametersOnGenericTypes
- CA1005
ms.assetid: 372b2f28-5c59-4815-9753-6c65b2bb3589
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b5fad132dfdda0ef12e6d74c503c5d27024a8382
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="ca1005-avoid-excessive-parameters-on-generic-types"></a>CA1005: Evite parámetros excesivos en tipos genéricos
|||  
|-|-|  
|TypeName|AvoidExcessiveParametersOnGenericTypes|  
|Identificador de comprobación|CA1005|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 Un tipo genérico visible externamente tiene más de dos parámetros de tipo.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Cuantos más parámetros type contenga un tipo genérico, más difícil resulta saber y recordar qué representa cada uno de ellos. Esto resulta evidente normalmente con un parámetro de tipo, como en `List<T>`y en algunos casos con dos parámetros de tipo, como en `Dictionary<TKey, TValue>`. Si hay más de dos parámetros de tipo, la dificultad se vuelve demasiado grande para la mayoría de los usuarios (por ejemplo, `TooManyTypeParameters<T, K, V>` en C# o `TooManyTypeParameters(Of T, K, V)` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, cambie el diseño que se va a utilizar no más de dos parámetros de tipo.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla a menos que el diseño requiera absolutamente más de dos parámetros de tipo. Al proporcionar genéricos con una sintaxis que sea fácil de entender y usar reduce el tiempo que se necesita para obtener información y aumenta la velocidad de adopción de nuevas bibliotecas.  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [CA1010: Las colecciones deben implementar la interfaz genérica](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000: No declarar miembros estáticos en tipos genéricos](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: No exponer listas genéricas](../code-quality/ca1002-do-not-expose-generic-lists.md)  
  
 [CA1006: No anidar tipos genéricos en firmas de miembro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004: Los métodos genéricos deben proporcionar un parámetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003: Utilizar instancias genéricas de controlador de eventos](../code-quality/ca1003-use-generic-event-handler-instances.md)  
  
 [CA1007: Utilizar valores genéricos cuando sea posible](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## <a name="see-also"></a>Vea también  
 [Genéricos](/dotnet/csharp/programming-guide/generics/index)