---
title: 'CA1021: Evitar los parámetros out'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 10ee8312a0861e65e0717cc6d9bec3d2530a8c80
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53911866"
---
# <a name="ca1021-avoid-out-parameters"></a>CA1021: Evitar los parámetros out

|||
|-|-|
|TypeName|AvoidOutParameters|
|Identificador de comprobación|CA1021|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un método público o protegido en un tipo público tiene un `out` parámetro.

## <a name="rule-description"></a>Descripción de la regla
 Pasar tipos por referencia (utilizando `out` o `ref`) requiere experiencia con punteros, saber la diferencia entre los tipos de valor y tipos de referencia y controlar métodos con varios valores devueltos. Además, la diferencia entre `out` y `ref` parámetros no se entiende ampliamente.

 Cuando se pasa un tipo de referencia "por referencia", el método intenta utilizar el parámetro para devolver una instancia diferente del objeto. Pasar un tipo de referencia por referencia también se conoce como mediante un doble puntero, puntero a un puntero o direccionamiento indirecto doble. Utilizando el valor predeterminado convención de llamada, que se pasa "por valor", un parámetro que toma un tipo de referencia recibe un puntero al objeto. El puntero, no el objeto al que señala, se pasa por valor. Pasar por valor significa que el método no puede cambiar el puntero para que señale a una nueva instancia del tipo de referencia. Sin embargo, puede cambiar el contenido del objeto al que señala. Para la mayoría de las aplicaciones, esto es suficiente y da como resultado el comportamiento deseado.

 Si un método debe devolver una instancia diferente, utilice el valor devuelto del método para realizar esta acción. Consulte la <xref:System.String?displayProperty=fullName> clase para una variedad de métodos que funcionan en cadenas y devolver una nueva instancia de una cadena. Cuando se usa este modelo, el llamador debe decidir si mantiene el objeto original.

 Aunque los valores devueltos son comunes y muy utilizados, la aplicación correcta de `out` y `ref` parámetros requiere un diseño intermedio y habilidades de programación. Arquitectos de bibliotecas para un público general no debería esperar que los usuarios dominen el uso de diseño `out` o `ref` parámetros.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla que se debe a un tipo de valor, que el método devuelve el objeto como su valor devuelto. Si el método debe devolver varios valores, vuelva a diseñar para que devuelva una única instancia de un objeto que contiene los valores.

 Para corregir una infracción de esta regla que se debe a un tipo de referencia, asegúrese de que es el comportamiento deseado devolver una nueva instancia de la referencia. Si es así, el método debe utilizar su valor devuelto para hacerlo.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 Es seguro suprimir una advertencia de esta regla. Sin embargo, este diseño podría provocar problemas de facilidad de uso.

## <a name="example"></a>Ejemplo
 La siguiente biblioteca muestra dos implementaciones de una clase que genera las respuestas a los comentarios de un usuario. La primera implementación (`BadRefAndOut`) obliga al usuario de la biblioteca para administrar los tres valores devueltos. La segunda implementación (`RedesignedRefAndOut`) simplifica la experiencia del usuario al devolver una instancia de una clase de contenedor (`ReplyData`) que administra los datos como una sola unidad.

 [!code-csharp[FxCop.Design.NoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_1.cs)]

## <a name="example"></a>Ejemplo
 La aplicación siguiente muestra la experiencia del usuario. La llamada a la biblioteca rediseñada (`UseTheSimplifiedClass` método) es más sencillo, y se administra fácilmente la información devuelta por el método. El resultado de los dos métodos es idéntico.

 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_2.cs)]

## <a name="example"></a>Ejemplo
 La biblioteca de ejemplo siguiente se muestra cómo `ref` parámetros para tipos de referencia se utilizan y se muestra una mejor manera de implementar esta funcionalidad.

 [!code-csharp[FxCop.Design.RefByRefNo#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_3.cs)]

## <a name="example"></a>Ejemplo
 La siguiente aplicación llama a cada método en la biblioteca para mostrar el comportamiento.

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

## <a name="try-pattern-methods"></a>Pruebe los métodos de patrón

### <a name="description"></a>Descripción
 Los métodos que implementan el **intente\<algo >** modelo, como <xref:System.Int32.TryParse%2A?displayProperty=fullName>, no producir esta infracción. El ejemplo siguiente muestra una estructura (tipo de valor) que implementa el <xref:System.Int32.TryParse%2A?displayProperty=fullName> método.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Design.TryPattern#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_5.cs)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1045: No pasar tipos por referencia](../code-quality/ca1045-do-not-pass-types-by-reference.md)