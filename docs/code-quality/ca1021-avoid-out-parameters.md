---
title: 'CA1021: Evitar parámetros out'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
ms.openlocfilehash: 86503ae5abb994b5b1d687744371a57ff6086e43
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="ca1021-avoid-out-parameters"></a>CA1021: Evitar parámetros out
|||
|-|-|
|TypeName|AvoidOutParameters|
|Identificador de comprobación|CA1021|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un método público o protegido en un tipo público tiene un `out` parámetro.

## <a name="rule-description"></a>Descripción de la regla
 Pasar tipos por referencia (utilizando `out` o `ref`) es necesario tener experiencia con punteros, saber la diferencia entre los tipos de valor y tipos de referencia y controlar métodos con varios valores devueltos. Además, la diferencia entre `out` y `ref` parámetros no se entiende ampliamente.

 Cuando se pasa un tipo de referencia "por referencia", el método intenta usar el parámetro para devolver una instancia diferente del objeto. Para pasar un tipo de referencia por referencia también se conoce como utilizar un puntero doble, puntero a un puntero, o el direccionamiento indirecto doble. Por medio del predeterminado convención de llamada, que se pasa "por valor", un parámetro que toma un tipo de referencia recibe un puntero al objeto. El puntero, no el objeto al que señala, se pasa por valor. Pasar por valor significa que el método no puede cambiar el puntero para que señale a una nueva instancia del tipo de referencia. Sin embargo, puede cambiar el contenido del objeto al que señala. Para la mayoría de las aplicaciones, esto es suficiente y da como resultado el comportamiento deseado.

 Si un método debe devolver una instancia diferente, utilice el valor devuelto del método para lograrlo. Consulte la <xref:System.String?displayProperty=fullName> clase para una amplia variedad de métodos que operan con cadenas y devuelve una nueva instancia de una cadena. Cuando se usa este modelo, el llamador debe decidir si se conserva el objeto original.

 Aunque los valores devueltos son comunes y muy utilizados, la aplicación correcta de `out` y `ref` parámetros requiere diseño intermedio y conocimiento del código. Los arquitectos de bibliotecas cuyos diseños están para una audiencia general no debe esperar que los usuarios dominen el uso `out` o `ref` parámetros.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla que se debe a un tipo de valor, que el método devuelve el objeto como su valor devuelto. Si el método debe devolver varios valores, vuelva a diseñar para devolver una única instancia de un objeto que contiene los valores.

 Para corregir una infracción de esta regla que se debe a un tipo de referencia, asegúrese de que es el comportamiento deseado devolver una nueva instancia de la referencia. Si es así, el método debe utilizar su valor devuelto para ello.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla. Sin embargo, este diseño podría provocar problemas de facilidad de uso.

## <a name="example"></a>Ejemplo
 La siguiente biblioteca muestra dos implementaciones de una clase que genera las respuestas a los comentarios de un usuario. La primera implementación (`BadRefAndOut`) obliga al usuario de la biblioteca a administrar tres valores devueltos. La segunda implementación (`RedesignedRefAndOut`) simplifica la experiencia del usuario mediante la devolución de una instancia de una clase de contenedor (`ReplyData`) que administra los datos como una sola unidad.

 [!code-csharp[FxCop.Design.NoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_1.cs)]

## <a name="example"></a>Ejemplo
 La aplicación siguiente muestra la experiencia del usuario. La llamada a la biblioteca rediseñada (`UseTheSimplifiedClass` método) es más sencillo, y se administra fácilmente la información devuelta por el método. El resultado de los dos métodos es idéntico.

 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_2.cs)]

## <a name="example"></a>Ejemplo
 La biblioteca de ejemplo siguiente se muestra cómo `ref` parámetros para los tipos de referencia se utilizan y muestra una manera mejor de implementar esta funcionalidad.

 [!code-csharp[FxCop.Design.RefByRefNo#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_3.cs)]

## <a name="example"></a>Ejemplo
 La aplicación siguiente llama a cada método en la biblioteca para mostrar el comportamiento.

 [!code-csharp[FxCop.Design.TestRefByRefNo#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_4.cs)]

 Este ejemplo produce el siguiente resultado:

 **Puntero de Changing - pasan por valor:**
**12345**
**12345**
**puntero Changing - pasado por referencia:** 
 ** 12345**
**ABCDE 12345**
**para pasar por valor devuelto:**
**ABCDE 12345**
## <a name="try-pattern-methods"></a>Pruebe los métodos de patrón

### <a name="description"></a>Descripción
 Métodos que implementan el **intente\<algo >** patrón, como <xref:System.Int32.TryParse%2A?displayProperty=fullName>, no producir esta infracción. En el ejemplo siguiente se muestra una estructura (tipo de valor) que implementa el <xref:System.Int32.TryParse%2A?displayProperty=fullName> método.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Design.TryPattern#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_5.cs)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1045: No pasar tipos por referencia](../code-quality/ca1045-do-not-pass-types-by-reference.md)