---
title: 'CA1000: no declarar miembros estáticos en tipos genéricos | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1000
- DoNotDeclareStaticMembersOnGenericTypes
helpviewer_keywords:
- DoNotDeclareStaticMembersOnGenericTypes
- CA1000
ms.assetid: 5c0da594-f8d0-4f40-953d-56bf7fbd2087
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1ef6c98c2808e639570b51d485df90bbdab72c43
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646363"
---
# <a name="ca1000-do-not-declare-static-members-on-generic-types"></a>CA1000: No declarar miembros estáticos en tipos genéricos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotDeclareStaticMembersOnGenericTypes|
|Identificador de comprobación|CA1000|
|Categoría|Microsoft. Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo genérico visible externamente contiene un miembro `static` (`Shared` en Visual Basic).

## <a name="rule-description"></a>Descripción de la regla
 Cuando se llama a un miembro de `static` de un tipo genérico, se debe especificar el argumento de tipo para el tipo. Cuando se llama a un miembro de instancia genérico que no admite la interferencia, se debe especificar el argumento de tipo para el miembro. La sintaxis para especificar el argumento de tipo en estos dos casos es diferente y se confunde fácilmente, como se muestra en las siguientes llamadas:

```vb
' Shared method in a generic type.
GenericType(Of Integer).SharedMethod()

' Generic instance method that does not support inference.
someObject.GenericMethod(Of Integer)()
```

```csharp
// Static method in a generic type.
GenericType<int>.StaticMethod();

// Generic instance method that does not support inference.
someObject.GenericMethod<int>();
```

 Por lo general, se deben evitar las dos declaraciones anteriores para que no sea necesario especificar el argumento de tipo cuando se llama al miembro. Esto da como resultado una sintaxis para llamar a miembros en genéricos que no son diferentes de la sintaxis de los elementos no genéricos. Para obtener más información, vea [CA1004: los métodos genéricos deben proporcionar un parámetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md).

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, quite el miembro estático o cámbielo por un miembro de instancia.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla. Proporcionar genéricos en una sintaxis que sea fácil de entender y usar reduce el tiempo necesario para aprender y aumentar la tasa de adopción de nuevas bibliotecas.

## <a name="related-rules"></a>Reglas relacionadas
 [CA1005: Evite parámetros excesivos en tipos genéricos](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Las colecciones deben implementar la interfaz genérica](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1002: No exponer listas genéricas](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: No anidar tipos genéricos en firmas de miembro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Los métodos genéricos deben proporcionar un parámetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Utilizar instancias genéricas de controlador de eventos](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: Utilizar valores genéricos cuando sea posible](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Vea también
 [Genéricos](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
