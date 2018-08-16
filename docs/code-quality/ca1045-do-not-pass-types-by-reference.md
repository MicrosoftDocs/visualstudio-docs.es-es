---
title: 'CA1045: No pasar tipos por referencia'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1045
- DoNotPassTypesByReference
helpviewer_keywords:
- CA1045
- DoNotPassTypesByReference
ms.assetid: bcc3900a-e092-4bb8-896f-cb83f6289968
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ddb9a54b440e4b76ebfac8300278483cf166d4d7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31900586"
---
# <a name="ca1045-do-not-pass-types-by-reference"></a>CA1045: No pasar tipos por referencia
|||
|-|-|
|TypeName|DoNotPassTypesByReference|
|Identificador de comprobación|CA1045|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un método público o protegido en un tipo público tiene un `ref` parámetro que toma un tipo primitivo, un tipo de referencia o un tipo de valor que no es uno de los tipos integrados.

## <a name="rule-description"></a>Descripción de la regla
 Pasar tipos por referencia (utilizando `out` o `ref`) es necesario tener experiencia con punteros, saber la diferencia entre los tipos de valor y tipos de referencia y controlar métodos con varios valores devueltos. Además, la diferencia entre `out` y `ref` parámetros no se entiende ampliamente.

 Cuando se pasa un tipo de referencia "por referencia", el método intenta usar el parámetro para devolver una instancia diferente del objeto. (Para pasar un tipo de referencia por referencia también se conoce como utilizar un puntero doble, puntero a un puntero, o el direccionamiento indirecto doble.) Usar el valor predeterminado convención de llamada, que se pasa "por valor", un parámetro que toma un tipo de referencia recibe un puntero al objeto. El puntero, no el objeto al que señala, se pasa por valor. Para pasar por valor significa que el método no puede cambiar el puntero para que señale a una nueva instancia de la referencia de tipo, pero sí puede cambiar el contenido del objeto al que señala. Para la mayoría de las aplicaciones, esto es suficiente y da como resultado el comportamiento que desee.

 Si un método debe devolver una instancia diferente, utilice el valor devuelto del método para lograrlo. Consulte la <xref:System.String?displayProperty=fullName> clase para una amplia variedad de métodos que operan con cadenas y devuelve una nueva instancia de una cadena. Con este modelo, se deja al llamador que decida si se conserva el objeto original.

 Aunque los valores devueltos son comunes y muy utilizados, la aplicación correcta de `out` y `ref` parámetros requiere diseño intermedio y conocimiento del código. Los arquitectos de bibliotecas cuyos diseños están para una audiencia general no debe esperar que los usuarios dominen el uso `out` o `ref` parámetros.

> [!NOTE]
>  Cuando se trabaja con parámetros que son estructuras largas, los recursos adicionales necesarios para copiar estas estructuras pudieron producir un efecto de rendimiento cuando se pasa por valor. En estos casos, podría considerar usar `ref` o `out` parámetros.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla que se debe a un tipo de valor, que el método devuelve el objeto como su valor devuelto. Si el método debe devolver varios valores, vuelva a diseñar para devolver una única instancia de un objeto que contiene los valores.

 Para corregir una infracción de esta regla que se debe a un tipo de referencia, asegúrese de que es el comportamiento que desee devolver una nueva instancia de la referencia. Si es así, el método debe utilizar su valor devuelto para ello.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla; Sin embargo, este diseño podría provocar problemas de facilidad de uso.

## <a name="example"></a>Ejemplo
 La siguiente biblioteca muestra dos implementaciones de una clase que genera las respuestas a los comentarios del usuario. La primera implementación (`BadRefAndOut`) obliga al usuario de la biblioteca a administrar tres valores devueltos. La segunda implementación (`RedesignedRefAndOut`) simplifica la experiencia del usuario mediante la devolución de una instancia de una clase de contenedor (`ReplyData`) que administra los datos como una sola unidad.

 [!code-csharp[FxCop.Design.NoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_1.cs)]

## <a name="example"></a>Ejemplo
 La aplicación siguiente muestra la experiencia del usuario. La llamada a la biblioteca rediseñada (`UseTheSimplifiedClass` método) es más sencillo, y se administra fácilmente la información devuelta por el método. El resultado de los dos métodos es idéntico.

 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_2.cs)]

## <a name="example"></a>Ejemplo
 La biblioteca de ejemplo siguiente se muestra cómo `ref` se usan parámetros de los tipos de referencia y muestra una manera mejor de implementar esta funcionalidad.

 [!code-csharp[FxCop.Design.RefByRefNo#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_3.cs)]

## <a name="example"></a>Ejemplo
 La aplicación siguiente llama a cada método en la biblioteca para mostrar el comportamiento.

 [!code-csharp[FxCop.Design.TestRefByRefNo#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_4.cs)]

 Este ejemplo produce el siguiente resultado:

 **Puntero de Changing - pasan por valor:**
**12345**
**12345**
**puntero Changing - pasado por referencia:** 
 ** 12345**
**ABCDE 12345**
**para pasar por valor devuelto:**
**ABCDE 12345**
## <a name="related-rules"></a>Reglas relacionadas
 [CA1021: Evitar parámetros out](../code-quality/ca1021-avoid-out-parameters.md)