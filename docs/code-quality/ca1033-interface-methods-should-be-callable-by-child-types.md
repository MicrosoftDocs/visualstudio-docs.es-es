---
title: 'CA1033: Los tipos secundarios deberían poder llamar a los métodos de interfaz'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d2c1a622519e08d4b56fdd8e6811ec039f9d3871
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="ca1033-interface-methods-should-be-callable-by-child-types"></a>CA1033: Los tipos secundarios deberían poder llamar a los métodos de interfaz
|||
|-|-|
|TypeName|InterfaceMethodsShouldBeCallableByChildTypes|
|Identificador de comprobación|CA1033|
|Categoría|Microsoft.Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un tipo no sellado visible externamente proporciona un método explícito de implementación de una interfaz pública pero no proporciona un método visible externamente alternativo con el mismo nombre.

## <a name="rule-description"></a>Descripción de la regla
 Considere la posibilidad de un tipo base que implementa explícitamente un método de interfaz pública. Un tipo que deriva del tipo base puede tener acceso al método de interfaz heredada sólo a través de una referencia a la instancia actual (`this` en C#) que se convierte en la interfaz. Si el tipo derivado vuelve a implementa (explícitamente) el método de interfaz heredada, la implementación base ya no son accesibles. La llamada a través de la referencia a la instancia actual invocará la implementación derivada; Esto hace que la recursividad y un desbordamiento de pila final.

 Esta regla no informa de una infracción de una implementación explícita de <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> cuando visible externamente `Close()` o `System.IDisposable.Dispose(Boolean)` se proporciona el método.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, implemente un nuevo método que expone la misma funcionalidad y es visible para los tipos derivados o cambiar a una implementación no explícitos. Si un cambio principal es aceptable, una alternativa es hacer que el tipo sealed.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si un método visible externamente está siempre tenga la misma funcionalidad pero con un nombre distinto del método implementado explícitamente.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un tipo, `ViolatingBase`, que infringe la regla y un tipo, `FixedBase`, que muestra una corrección para la infracción.

 [!code-csharp[FxCop.Design.ExplicitMethodImplementations#1](../code-quality/codesnippet/CSharp/ca1033-interface-methods-should-be-callable-by-child-types_1.cs)]

## <a name="see-also"></a>Vea también
 [Interfaces](/dotnet/csharp/programming-guide/interfaces/index)