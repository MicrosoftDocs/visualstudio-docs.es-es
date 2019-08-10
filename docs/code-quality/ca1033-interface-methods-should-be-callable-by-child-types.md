---
title: 'CA1033: Los tipos secundarios deben poder llamar a los métodos de interfaz'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InterfaceMethodsShouldBeCallableByChildTypes
- CA1033
helpviewer_keywords:
- CA1033
- InterfaceMethodsShouldBeCallableByChildTypes
ms.assetid: 9f171497-a5e3-4769-a77b-7aed755b2662
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 10db644fe4cf65a7336ef8bd50dcf62e072e1c46
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922951"
---
# <a name="ca1033-interface-methods-should-be-callable-by-child-types"></a>CA1033: Los tipos secundarios deben poder llamar a los métodos de interfaz

|||
|-|-|
|TypeName|InterfaceMethodsShouldBeCallableByChildTypes|
|Identificador de comprobación|CA1033|
|Categoría|Microsoft.Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
Un tipo no sellado visible externamente proporciona un método explícito de implementación de una interfaz pública pero no proporciona un método visible externamente alternativo con el mismo nombre.

## <a name="rule-description"></a>Descripción de la regla
Considere un tipo base que implementa explícitamente un método de interfaz pública. Un tipo que se deriva del tipo base solo puede tener acceso al método de interfaz heredado a través de una referencia a`this` la C#instancia actual (en) que se convierte en la interfaz. Si el tipo derivado implementa (explícitamente) el método de interfaz heredado, ya no se puede tener acceso a la implementación base. La llamada a través de la referencia de la instancia actual invocará la implementación derivada; Esto produce una recursividad y un desbordamiento de pila eventual.

Esta regla no notifica una infracción de una implementación explícita de <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> cuando se proporciona un método `Close()` o `System.IDisposable.Dispose(Boolean)` visible externamente.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, implemente un nuevo método que exponga la misma funcionalidad y sea visible para los tipos derivados o cambie a una implementación no explícita. Si un cambio importante es aceptable, una alternativa es convertir el tipo en sellado.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Es seguro suprimir una advertencia de esta regla si se proporciona un método visible externamente con la misma funcionalidad pero con un nombre diferente del método implementado explícitamente.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra un `ViolatingBase`tipo,, que infringe la regla y un tipo `FixedBase`,, que muestra una corrección para la infracción.

[!code-csharp[FxCop.Design.ExplicitMethodImplementations#1](../code-quality/codesnippet/CSharp/ca1033-interface-methods-should-be-callable-by-child-types_1.cs)]

## <a name="see-also"></a>Vea también
[Interfaces](/dotnet/csharp/programming-guide/interfaces/index)