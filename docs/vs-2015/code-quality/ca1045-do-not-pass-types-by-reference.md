---
title: 'CA1045: No pasar tipos por referencia | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1045
- DoNotPassTypesByReference
helpviewer_keywords:
- CA1045
- DoNotPassTypesByReference
ms.assetid: bcc3900a-e092-4bb8-896f-cb83f6289968
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6bbdcb2e2ac8f905a2b52cfb41ed90217d215b4b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431540"
---
# <a name="ca1045-do-not-pass-types-by-reference"></a>CA1045: No pasar tipos por referencia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotPassTypesByReference|
|Identificador de comprobación|CA1045|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un método público o protegido en un tipo público tiene un `ref` parámetro que toma un tipo primitivo, un tipo de referencia o un tipo de valor que no es uno de los tipos integrados.

## <a name="rule-description"></a>Descripción de la regla
 Pasar tipos por referencia (utilizando `out` o `ref`) es necesario tener experiencia con punteros, saber la diferencia entre los tipos de valor y tipos de referencia y controlar los métodos que tienen varios valores devueltos. Además, la diferencia entre `out` y `ref` parámetros no se entiende ampliamente.

 Cuando se pasa un tipo de referencia "por referencia", el método intenta utilizar el parámetro para devolver una instancia diferente del objeto. (Pasar un tipo de referencia por referencia también se conoce como mediante un doble puntero, puntero a un puntero o direccionamiento indirecto doble.) Con el valor predeterminado convención de llamada, que se pasa "por valor", un parámetro que toma un tipo de referencia recibe un puntero al objeto. El puntero, no el objeto al que señala, se pasa por valor. Pasar por valor significa que el método no puede cambiar el puntero para que señale a una nueva instancia de la referencia de tipo, pero sí puede cambiar el contenido del objeto al que señala. Para la mayoría de las aplicaciones, esto es suficiente y provoca el comportamiento que desee.

 Si un método debe devolver una instancia diferente, utilice el valor devuelto del método para realizar esta acción. Consulte la <xref:System.String?displayProperty=fullName> clase para una variedad de métodos que funcionan en cadenas y devolver una nueva instancia de una cadena. Con este modelo, se deja al autor de llamada para decidir si se conserva el objeto original.

 Aunque los valores devueltos son comunes y muy utilizados, la aplicación correcta de `out` y `ref` parámetros requiere un diseño intermedio y habilidades de programación. Arquitectos de bibliotecas para un público general no debería esperar que los usuarios dominen el uso de diseño `out` o `ref` parámetros.

> [!NOTE]
> Cuando se trabaja con parámetros que son estructuras de gran tamaño, los recursos adicionales necesarios para copiar estas estructuras podrían provocar un efecto de rendimiento cuando se pasa por valor. En estos casos, podría usar `ref` o `out` parámetros.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla que se debe a un tipo de valor, que el método devuelve el objeto como su valor devuelto. Si el método debe devolver varios valores, vuelva a diseñar para que devuelva una única instancia de un objeto que contiene los valores.

 Para corregir una infracción de esta regla que se debe a un tipo de referencia, asegúrese de que es el comportamiento que desee devolver una nueva instancia de la referencia. Si es así, el método debe utilizar su valor devuelto para hacerlo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla; Sin embargo, este diseño podría provocar problemas de facilidad de uso.

## <a name="example"></a>Ejemplo
 La siguiente biblioteca muestra dos implementaciones de una clase que genera las respuestas a los comentarios del usuario. La primera implementación (`BadRefAndOut`) obliga al usuario de la biblioteca para administrar los tres valores devueltos. La segunda implementación (`RedesignedRefAndOut`) simplifica la experiencia del usuario al devolver una instancia de una clase de contenedor (`ReplyData`) que administra los datos como una sola unidad.

 [!code-csharp[FxCop.Design.NoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NoRefOrOut/cs/FxCop.Design.NoRefOrOut.cs#1)]

## <a name="example"></a>Ejemplo
 La aplicación siguiente muestra la experiencia del usuario. La llamada a la biblioteca rediseñada (`UseTheSimplifiedClass` método) es más sencillo, y se administra fácilmente la información devuelta por el método. El resultado de los dos métodos es idéntico.

 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestNoRefOrOut/cs/FxCop.Design.TestNoRefOrOut.cs#1)]

## <a name="example"></a>Ejemplo
 La biblioteca de ejemplo siguiente se muestra cómo `ref` se usan parámetros para tipos de referencia y se muestra una mejor manera de implementar esta funcionalidad.

 [!code-csharp[FxCop.Design.RefByRefNo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RefByRefNo/cs/FxCop.Design.RefByRefNo.cs#1)]

## <a name="example"></a>Ejemplo
 La siguiente aplicación llama a cada método en la biblioteca para mostrar el comportamiento.

 [!code-csharp[FxCop.Design.TestRefByRefNo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestRefByRefNo/cs/FxCop.Design.TestRefByRefNo.cs#1)]

 Este ejemplo produce el siguiente resultado:

 **Puntero Changing - pasa por valor:**
**12345**
**12345**
**puntero Changing - pasado por referencia:** 
 ** 12345**
**ABCDE 12345**
**pasar por valor devuelto:**
**ABCDE 12345**
## <a name="related-rules"></a>Reglas relacionadas
 [CA1021: Evitar parámetros out](../code-quality/ca1021-avoid-out-parameters.md)
