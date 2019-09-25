---
title: 'CA1021: Evitar los parámetros out'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1021
- AvoidOutParameters
helpviewer_keywords:
- AvoidOutParameters
- CA1021
ms.assetid: 970f2304-842c-4fb7-9734-f3871da8d479
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e333e53fea1b965b250bdc97924e93728d55805a
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236180"
---
# <a name="ca1021-avoid-out-parameters"></a>CA1021: Evitar los parámetros out

|||
|-|-|
|TypeName|AvoidOutParameters|
|Identificador de comprobación|CA1021|
|Categoría|Microsoft.Design|
|Cambio importante|Problemático|

## <a name="cause"></a>Motivo
Un método público o protegido en un tipo público tiene un `out` parámetro.

## <a name="rule-description"></a>Descripción de la regla
Pasar tipos por referencia (mediante `out` o `ref`) requiere experiencia con punteros, comprender cómo difieren los tipos de valor y de referencia, y cómo controlar métodos con varios valores devueltos. Además, la diferencia entre `out` los `ref` parámetros y no se comprende ampliamente.

Cuando se pasa un tipo de referencia "por referencia", el método pretende usar el parámetro para devolver una instancia diferente del objeto. Pasar un tipo de referencia por referencia también se conoce como usar un puntero doble, un puntero a un puntero o un doble direccionamiento indirecto. Mediante el uso de la Convención de llamada predeterminada, que es Pass "by value", un parámetro que toma un tipo de referencia ya recibe un puntero al objeto. El puntero, no el objeto al que señala, se pasa por valor. Pasar por valor significa que el método no puede cambiar el puntero para que apunte a una nueva instancia del tipo de referencia. Sin embargo, puede cambiar el contenido del objeto al que señala. Para la mayoría de las aplicaciones, esto es suficiente y produce el comportamiento deseado.

Si un método debe devolver una instancia diferente, utilice el valor devuelto del método para lograrlo. Vea la <xref:System.String?displayProperty=fullName> clase para obtener una serie de métodos que operan en cadenas y devuelven una nueva instancia de una cadena. Cuando se usa este modelo, el autor de la llamada debe decidir si se conserva el objeto original.

Aunque los valores devueltos son comunes y muy utilizados, la `out` aplicación `ref` correcta de los parámetros y requiere conocimientos intermedios de diseño y codificación. Los arquitectos de biblioteca que diseñan para un público general no deben esperar que los `out` usuarios `ref` dominen el trabajo con los parámetros o.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla causada por un tipo de valor, haga que el método devuelva el objeto como su valor devuelto. Si el método debe devolver varios valores, vuelva a diseñarlo para devolver una única instancia de un objeto que contiene los valores.

Para corregir una infracción de esta regla causada por un tipo de referencia, asegúrese de que el comportamiento deseado es devolver una nueva instancia de la referencia. Si es así, el método debería usar su valor devuelto para hacerlo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Es seguro suprimir una advertencia de esta regla. Sin embargo, este diseño podría provocar problemas de facilidad de uso.

## <a name="example"></a>Ejemplo
En la biblioteca siguiente se muestran dos implementaciones de una clase que genera respuestas a los comentarios de un usuario. La primera implementación (`BadRefAndOut`) obliga al usuario de la biblioteca a administrar tres valores devueltos. La segunda implementación (`RedesignedRefAndOut`) simplifica la experiencia del usuario al devolver una instancia de una clase contenedora`ReplyData`() que administra los datos como una sola unidad.

[!code-csharp[FxCop.Design.NoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_1.cs)]

## <a name="example"></a>Ejemplo
La siguiente aplicación muestra la experiencia del usuario. La llamada a la biblioteca rediseñada (`UseTheSimplifiedClass` método) es más sencilla y la información devuelta por el método se administra fácilmente. La salida de los dos métodos es idéntica.

[!code-csharp[FxCop.Design.TestNoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_2.cs)]

## <a name="example"></a>Ejemplo
En la biblioteca de ejemplo siguiente se `ref` muestra cómo se usan los parámetros para los tipos de referencia y se muestra una mejor manera de implementar esta funcionalidad.

[!code-csharp[FxCop.Design.RefByRefNo#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_3.cs)]

## <a name="example"></a>Ejemplo
La siguiente aplicación llama a cada método de la biblioteca para mostrar el comportamiento.

[!code-csharp[FxCop.Design.TestRefByRefNo#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_4.cs)]

Este ejemplo produce el siguiente resultado:

```txt
Changing pointer - passed by value:
12345
12345
Changing pointer - passed by reference:
12345
12345 ABCDE
Passing by return value:
12345 ABCDE
```

## <a name="try-pattern-methods"></a>Probar métodos de patrón

### <a name="description"></a>Descripción
Los métodos que implementan el <xref:System.Int32.TryParse%2A?displayProperty=fullName>patrón **try\<algo >** , como, no provocan esta infracción. En el ejemplo siguiente se muestra una estructura (tipo de valor) que <xref:System.Int32.TryParse%2A?displayProperty=fullName> implementa el método.

### <a name="code"></a>Código
[!code-csharp[FxCop.Design.TryPattern#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_5.cs)]

## <a name="related-rules"></a>Reglas relacionadas
[CA1045: No pasar tipos por referencia](../code-quality/ca1045-do-not-pass-types-by-reference.md)