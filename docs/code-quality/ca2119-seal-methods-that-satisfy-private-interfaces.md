---
title: 'CA2119: Sellar los métodos que cumplan las interfaces privadas'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6f6abbb7a6ada80bf274577c8b9134af29b944ec
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="ca2119-seal-methods-that-satisfy-private-interfaces"></a>CA2119: Sellar los métodos que cumplan las interfaces privadas
|||
|-|-|
|TypeName|SealMethodsThatSatisfyPrivateInterfaces|
|Identificador de comprobación|CA2119|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo público heredable proporciona una implementación de método reemplazable de una `internal` (`Friend` en Visual Basic) (interfaz).

## <a name="rule-description"></a>Descripción de la regla
 Métodos de interfaz tienen accesibilidad pública, que no se puede cambiar el tipo de implementación. Una interfaz interna crea un contrato que no está previsto su implementación fuera del ensamblado que define la interfaz. Un tipo público que implementa un método de una interfaz interna con la `virtual` (`Overridable` en Visual Basic) modificador permite que el método que sea reemplazado por un tipo derivado que está fuera del ensamblado. Si un segundo tipo del ensamblado de definición llama al método y espera un contrato solo para uso interno, se verían comprometido comportamiento cuando, en su lugar, se ejecuta el método invalidado en el ensamblado externo. Esto crea una vulnerabilidad de seguridad.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, impida el método se invalide fuera del ensamblado mediante el uso de uno de los siguientes:

-   Hacer que el tipo declarativo `sealed` (`NotInheritable` en Visual Basic).

-   Cambie la accesibilidad del tipo declarativo a `internal` (`Friend` en Visual Basic).

-   Quite todos los constructores públicos del tipo declarativo.

-   Implemente el método sin utilizar el `virtual` modificador.

-   Implemente el método explícitamente.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si, después de una revisión cuidadosa, existe ningún problema de seguridad que puede ser explotable si el método se invalide fuera del ensamblado.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un tipo, `BaseImplementation`, que infringe esta regla.

 [!code-cpp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_1.cpp)]
 [!code-csharp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_1.cs)]
 [!code-vb[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_1.vb)]

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se aprovecha la implementación del método virtual del ejemplo anterior.

 [!code-cpp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_2.cpp)]
 [!code-csharp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_2.cs)]
 [!code-vb[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_2.vb)]

## <a name="see-also"></a>Vea también
 [Interfaces](/dotnet/csharp/programming-guide/interfaces/index) [Interfaces](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)