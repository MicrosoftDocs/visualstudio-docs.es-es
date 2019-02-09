---
title: 'CA2119: Sellar los métodos que satisfacen las interfaces privadas'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SealMethodsThatSatisfyPrivateInterfaces
- CA2119
helpviewer_keywords:
- CA2119
- SealMethodsThatSatisfyPrivateInterfaces
ms.assetid: 483d02e1-cfaf-4754-a98f-4116df0f3509
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 4c019e98e7f1311b6521dff563cb8e7bb0a2356e
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55952052"
---
# <a name="ca2119-seal-methods-that-satisfy-private-interfaces"></a>CA2119: Sellar los métodos que satisfacen las interfaces privadas

|||
|-|-|
|TypeName|SealMethodsThatSatisfyPrivateInterfaces|
|Identificador de comprobación|CA2119|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo público heredable proporciona una implementación de método reemplazable de una `internal` (`Friend` en Visual Basic) interfaz.

## <a name="rule-description"></a>Descripción de la regla
 Los métodos de interfaz tienen accesibilidad pública, que no se puede cambiar el tipo de implementación. Una interfaz interna crea un contrato que no está pensado para implementarse fuera del ensamblado que define la interfaz. Un tipo público que implemente un método de una interfaz interna con el `virtual` (`Overridable` en Visual Basic) modificador permite que el método que sea reemplazado por un tipo derivado que está fuera del ensamblado. Si un segundo tipo en el ensamblado de definición llama al método y espera un contrato solo para uso interno, comportamiento podría estar en peligro cuando, en su lugar, se ejecuta el método invalidado en el ensamblado externo. Esto crea una vulnerabilidad de seguridad.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, evitar que el método se invalide fuera del ensamblado utilizando uno de los siguientes:

- Convierta el tipo declarativo `sealed` (`NotInheritable` en Visual Basic).

- Cambie la accesibilidad del tipo declarativo para `internal` (`Friend` en Visual Basic).

- Quite todos los constructores públicos del tipo declarativo.

- Implemente el método sin utilizar el `virtual` modificador.

- Implementar el método de forma explícita.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si, tras una revisión exhaustiva, existe ningún problema de seguridad que puede ser aprovechable si se reemplaza el método fuera del ensamblado.

## <a name="example-1"></a>Ejemplo 1
 El ejemplo siguiente muestra un tipo, `BaseImplementation`, que infringe esta regla.

 [!code-cpp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_1.cpp)]
 [!code-csharp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_1.cs)]
 [!code-vb[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_1.vb)]

## <a name="example-2"></a>Ejemplo 2
 El ejemplo siguiente aprovecha la implementación del método virtual del ejemplo anterior.

 [!code-cpp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_2.cpp)]
 [!code-csharp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_2.cs)]
 [!code-vb[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_2.vb)]

## <a name="see-also"></a>Vea también

- [Interfaces](/dotnet/csharp/programming-guide/interfaces/index)
- [Interfaces](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)