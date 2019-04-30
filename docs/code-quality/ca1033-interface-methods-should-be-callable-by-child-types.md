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
ms.openlocfilehash: 1fd8ee08b53ef3f9216edcb67ebcdbe6c4978bb3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62778849"
---
# <a name="ca1033-interface-methods-should-be-callable-by-child-types"></a>CA1033: Los tipos secundarios deben poder llamar a los métodos de interfaz

|||
|-|-|
|TypeName|InterfaceMethodsShouldBeCallableByChildTypes|
|Identificador de comprobación|CA1033|
|Categoría|Microsoft.Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un tipo no sellado visible externamente proporciona un método explícito de implementación de una interfaz pública pero no proporciona un método visible externamente alternativo con el mismo nombre.

## <a name="rule-description"></a>Descripción de la regla
 Considere la posibilidad de un tipo base que implementa explícitamente un método de interfaz pública. Un tipo que deriva el tipo base puede tener acceso al método de interfaz heredados sólo a través de una referencia a la instancia actual (`this` en C#) que se convierte en la interfaz. Si el tipo derivado vuelva a implementar (explícitamente) el método de interfaz heredada, ya no se puede acceder la implementación base. La llamada a través de la referencia a la instancia actual invocará la implementación derivada; Esto hace que la recursividad y el desbordamiento de la pila.

 Esta regla no informa de una infracción en una implementación explícita de <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> cuando visible externamente `Close()` o `System.IDisposable.Dispose(Boolean)` se proporciona el método.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, implemente un nuevo método que expone la misma funcionalidad y es visible para los tipos derivados o cambiar a una implementación no explícitos. Si un cambio importante es aceptable, una alternativa es hacer que el tipo como sellado.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si se proporciona tiene la misma funcionalidad, pero un nombre distinto del método implementado explícitamente un método visible externamente.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un tipo, `ViolatingBase`, que infringe la regla y un tipo, `FixedBase`, que muestra una corrección de la infracción.

 [!code-csharp[FxCop.Design.ExplicitMethodImplementations#1](../code-quality/codesnippet/CSharp/ca1033-interface-methods-should-be-callable-by-child-types_1.cs)]

## <a name="see-also"></a>Vea también
 [Interfaces](/dotnet/csharp/programming-guide/interfaces/index)