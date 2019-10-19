---
title: 'CA1045: no pasar tipos por referencia | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 259e0d17ccf71518759ac192ee87a6ef5b921b23
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668281"
---
# <a name="ca1045-do-not-pass-types-by-reference"></a>CA1045: No pasar tipos por referencia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotPassTypesByReference|
|Identificador de comprobación|CA1045|
|Categoría|Microsoft. Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un método público o protegido en un tipo público tiene un `ref` parámetro que toma un tipo primitivo, un tipo de referencia o un tipo de valor que no es uno de los tipos integrados.

## <a name="rule-description"></a>Descripción de la regla
 Pasar tipos por referencia (mediante `out` o `ref`) requiere experiencia con punteros, comprender cómo difieren los tipos de valor y los tipos de referencia, y cómo controlar los métodos que tienen varios valores devueltos. Además, la diferencia entre los parámetros `out` y `ref` no se comprende ampliamente.

 Cuando se pasa un tipo de referencia "por referencia", el método pretende usar el parámetro para devolver una instancia diferente del objeto. (El paso de un tipo de referencia por referencia también se conoce como el uso de un puntero doble, un puntero a un puntero o un direccionamiento indirecto doble). Mediante la Convención de llamada predeterminada, que es Pass "by value", un parámetro que toma un tipo de referencia ya recibe un puntero al objeto. El puntero, no el objeto al que señala, se pasa por valor. Pasar por valor significa que el método no puede cambiar el puntero para que apunte a una nueva instancia del tipo de referencia, pero puede cambiar el contenido del objeto al que señala. Para la mayoría de las aplicaciones, esto es suficiente y produce el comportamiento que se desea.

 Si un método debe devolver una instancia diferente, utilice el valor devuelto del método para lograrlo. Vea la clase <xref:System.String?displayProperty=fullName> para obtener una serie de métodos que operan en cadenas y devuelven una nueva instancia de una cadena. Con este modelo, se deja al autor de la llamada decidir si se conserva el objeto original.

 Aunque los valores devueltos son comunes y muy utilizados, la aplicación correcta de los parámetros `out` y `ref` requiere un diseño intermedio y conocimientos de codificación. Los arquitectos de biblioteca que diseñan para una audiencia general no deben esperar que los usuarios dominen el trabajo con `out` o `ref`.

> [!NOTE]
> Cuando se trabaja con parámetros que son estructuras grandes, los recursos adicionales necesarios para copiar estas estructuras podrían producir un efecto de rendimiento al pasar por valor. En estos casos, puede considerar el uso de `ref` o `out` parámetros.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla causada por un tipo de valor, haga que el método devuelva el objeto como su valor devuelto. Si el método debe devolver varios valores, vuelva a diseñarlo para devolver una única instancia de un objeto que contiene los valores.

 Para corregir una infracción de esta regla causada por un tipo de referencia, asegúrese de que el comportamiento que desea es devolver una nueva instancia de la referencia. Si es así, el método debería usar su valor devuelto para hacerlo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla. sin embargo, este diseño podría provocar problemas de facilidad de uso.

## <a name="example"></a>Ejemplo
 En la biblioteca siguiente se muestran dos implementaciones de una clase que genera respuestas a los comentarios del usuario. La primera implementación (`BadRefAndOut`) obliga al usuario de la biblioteca a administrar tres valores devueltos. La segunda implementación (`RedesignedRefAndOut`) simplifica la experiencia del usuario al devolver una instancia de una clase contenedora (`ReplyData`) que administra los datos como una sola unidad.

 [!code-csharp[FxCop.Design.NoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NoRefOrOut/cs/FxCop.Design.NoRefOrOut.cs#1)]

## <a name="example"></a>Ejemplo
 La siguiente aplicación muestra la experiencia del usuario. La llamada a la biblioteca rediseñada (método `UseTheSimplifiedClass`) es más sencilla y la información devuelta por el método se administra fácilmente. La salida de los dos métodos es idéntica.

 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestNoRefOrOut/cs/FxCop.Design.TestNoRefOrOut.cs#1)]

## <a name="example"></a>Ejemplo
 En la biblioteca de ejemplo siguiente se muestra cómo se usan los parámetros de `ref` para los tipos de referencia y se muestra una mejor manera de implementar esta funcionalidad.

 [!code-csharp[FxCop.Design.RefByRefNo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RefByRefNo/cs/FxCop.Design.RefByRefNo.cs#1)]

## <a name="example"></a>Ejemplo
 La siguiente aplicación llama a cada método de la biblioteca para mostrar el comportamiento.

 [!code-csharp[FxCop.Design.TestRefByRefNo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestRefByRefNo/cs/FxCop.Design.TestRefByRefNo.cs#1)]

 Este ejemplo produce el siguiente resultado:

 **Cambiar el puntero por valor:** 
**12345** 
**12345** 
**cambiar el puntero por referencia:** 
**12345** 
**12345 ABCDE** 1**pasar por valor devuelto: **3**12345 ABCDE**
## <a name="related-rules"></a>Reglas relacionadas
 [CA1021: Evitar parámetros out](../code-quality/ca1021-avoid-out-parameters.md)
