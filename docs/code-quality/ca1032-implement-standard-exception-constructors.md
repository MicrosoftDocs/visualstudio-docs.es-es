---
title: 'CA1032: Implementar constructores de excepción estándar'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1032
- ImplementStandardExceptionConstructors
helpviewer_keywords:
- CA1032
- ImplementStandardExceptionConstructors
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7baf13eb9125b273ad8fb1265a65eb7b053238a1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62779129"
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032: Implementar constructores de excepción estándar

|||
|-|-|
|TypeName|ImplementStandardExceptionConstructors|
|Identificador de comprobación|CA1032|
|Categoría|Microsoft.Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo

Extiende un tipo <xref:System.Exception?displayProperty=fullName> pero no declara todos los constructores necesarios.

## <a name="rule-description"></a>Descripción de la regla

Tipos de excepción deben implementar los tres constructores siguientes:

- NewException() pública

- NewException(string) pública

- pública NewException (string, excepción)

Además, si ejecuta el análisis de código estático de FxCop heredado como contraposición a [analizadores de FxCop basados en Roslyn](../code-quality/roslyn-analyzers-overview.md), la ausencia de un cuarto constructor también genera una infracción de:

- Protected o private NewException (SerializationInfo, StreamingContext)

El error al proporcionar el conjunto completo de constructores puede dificultar el control correcto de las excepciones. Por ejemplo, el constructor que tiene la firma `NewException(string, Exception)` se usa para crear las excepciones producidas por otras excepciones. Sin este constructor, no se puede crear y producir una instancia de la excepción personalizada que contiene una excepción interna (anidada), que es el código administrado debe hacer en esta situación.

Los primeros tres constructores de excepción son públicos por convención. El cuarto constructor está protegido en clases no selladas y private en clases selladas. Para obtener más información, consulte [CA2229: implementar constructores de serialización](../code-quality/ca2229-implement-serialization-constructors.md)

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, agregue los constructores que faltan a la excepción y asegúrese de que tienen la accesibilidad correcta.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Es seguro suprimir una advertencia de esta regla cuando se produjo la infracción de mediante el uso de un nivel de acceso diferente para los constructores públicos. Además, no pasa nada suprimir la advertencia para el `NewException(SerializationInfo, StreamingContext)` constructor si va a crear una biblioteca de clases Portable (PCL).

## <a name="example"></a>Ejemplo

El ejemplo siguiente contiene un tipo de excepción que infringe esta regla y un tipo de excepción que se implementa correctamente.

[!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../code-quality/codesnippet/CSharp/ca1032-implement-standard-exception-constructors_1.cs)]

## <a name="see-also"></a>Vea también

[CA2229: implementar constructores de serialización](../code-quality/ca2229-implement-serialization-constructors.md)