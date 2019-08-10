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
ms.openlocfilehash: 02e69a97468675cd6f7530793581c15717465d6f
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921059"
---
# <a name="ca2119-seal-methods-that-satisfy-private-interfaces"></a>CA2119: Sellar los métodos que satisfacen las interfaces privadas

|||
|-|-|
|TypeName|SealMethodsThatSatisfyPrivateInterfaces|
|Identificador de comprobación|CA2119|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
Un tipo público heredable proporciona una implementación de método reemplazable de `internal` una`Friend` interfaz (en Visual Basic).

## <a name="rule-description"></a>Descripción de la regla
Los métodos de interfaz tienen accesibilidad pública, que el tipo de implementación no puede cambiar. Una interfaz interna crea un contrato que no está diseñado para implementarse fuera del ensamblado que define la interfaz. Un tipo público que implementa un método de una interfaz interna mediante el `virtual` modificador (`Overridable` en Visual Basic) permite que un tipo derivado que está fuera del ensamblado invalide el método. Si un segundo tipo del ensamblado de definición llama al método y espera un contrato solo interno, el comportamiento puede verse comprometido cuando, en su lugar, se ejecuta el método invalidado en el ensamblado externo. Esto crea una vulnerabilidad de seguridad.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, evite que el método se invalide fuera del ensamblado mediante una de las siguientes acciones:

- Cree el tipo `sealed` declarativo`NotInheritable` (en Visual Basic).

- Cambie la accesibilidad del tipo declarativo a `internal` (`Friend` en Visual Basic).

- Quite todos los constructores públicos del tipo declarativo.

- Implemente el método sin usar `virtual` el modificador.

- Implemente el método explícitamente.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Es seguro suprimir una advertencia de esta regla si, después de una revisión cuidadosa, no existe ningún problema de seguridad que pueda ser aprovechable si el método se invalida fuera del ensamblado.

## <a name="example-1"></a>Ejemplo 1
En el ejemplo siguiente se muestra un `BaseImplementation`tipo,, que infringe esta regla.

[!code-cpp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_1.cpp)]
[!code-csharp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_1.cs)]
[!code-vb[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_1.vb)]

## <a name="example-2"></a>Ejemplo 2
En el ejemplo siguiente se aprovecha la implementación del método virtual del ejemplo anterior.

[!code-cpp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_2.cpp)]
[!code-csharp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_2.cs)]
[!code-vb[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_2.vb)]

## <a name="see-also"></a>Vea también

- [Interfaces](/dotnet/csharp/programming-guide/interfaces/index)
- [Interfaces](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)