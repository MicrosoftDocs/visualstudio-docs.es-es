---
title: 'CA1005: Evite parámetros excesivos en tipos genéricos | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- AvoidExcessiveParametersOnGenericTypes
- CA1005
helpviewer_keywords:
- AvoidExcessiveParametersOnGenericTypes
- CA1005
ms.assetid: 372b2f28-5c59-4815-9753-6c65b2bb3589
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d807fc581b6c4f0c06b2b2de1c86a148c30c4ff7
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591152"
---
# <a name="ca1005-avoid-excessive-parameters-on-generic-types"></a>CA1005: Evite parámetros excesivos en tipos genéricos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [CA1005: Evite parámetros excesivos en tipos genéricos](https://docs.microsoft.com/visualstudio/code-quality/ca1005-avoid-excessive-parameters-on-generic-types).

|||
|-|-|
|TypeName|AvoidExcessiveParametersOnGenericTypes|
|Identificador de comprobación|CA1005|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo genérico visible externamente tiene más de dos parámetros de tipo.

## <a name="rule-description"></a>Descripción de la regla
 Cuantos más parámetros de tipo contenga un tipo genérico, más difícil resulta saber y recordar qué representa cada uno de ellos. Suele ser evidente con un parámetro de tipo, como en `List<T>`y en algunos casos con dos parámetros de tipo, como en `Dictionary<TKey, TValue>`. Si existen más de dos parámetros de tipo, la dificultad se vuelve demasiado grande para la mayoría de los usuarios (por ejemplo, `TooManyTypeParameters<T, K, V>` en C# o `TooManyTypeParameters(Of T, K, V)` en [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]).

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie el diseño para utilizar no más de dos parámetros de tipo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima una advertencia de esta regla a menos que el diseño requiera absolutamente más de dos parámetros de tipo. Al proporcionar genéricos con una sintaxis fácil de entender y usar reduce el tiempo necesario para obtener información y aumenta la tasa de adopción de nuevas bibliotecas.

## <a name="related-rules"></a>Reglas relacionadas
 [CA1010: Las colecciones deben implementar la interfaz genérica](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: No declarar miembros estáticos en tipos genéricos](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: No exponer listas genéricas](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: No anidar tipos genéricos en firmas de miembro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Los métodos genéricos deben proporcionar un parámetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Utilizar instancias genéricas de controlador de eventos](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: Utilizar valores genéricos cuando sea posible](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Vea también
 [Genéricos](http://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)



