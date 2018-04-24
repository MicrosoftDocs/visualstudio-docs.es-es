---
title: 'CA1032: Implementar constructores de excepción estándar'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d140ab9f9ee5ef27332c59e30920fa89aebefdde
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032: Implementar constructores de excepción estándar
|||
|-|-|
|TypeName|ImplementStandardExceptionConstructors|
|Identificador de comprobación|CA1032|
|Categoría|Microsoft.Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un tipo extiende <xref:System.Exception?displayProperty=fullName> y no declara todos los constructores necesarios.

## <a name="rule-description"></a>Descripción de la regla
 Tipos de excepción deben implementar los constructores siguientes:

-   NewException() público

-   NewException(string) público

-   pública NewException (string, excepción)

-   Protected o private NewException (SerializationInfo, StreamingContext)

 El error al proporcionar el conjunto completo de constructores puede dificultar el control correcto de las excepciones. Por ejemplo, el constructor que tiene la firma `NewException(string, Exception)` se utiliza para crear las excepciones causadas por otras excepciones. Sin este constructor no puede crear y producir una instancia de la excepción personalizada que contiene una excepción interna (anidada), que es el código administrado debe hacer en esta situación. Los primeros tres constructores de excepción son públicos por convención. El cuarto constructor está protegido en clases no selladas y es privado en clases selladas. Para obtener más información, consulte [CA2229: implementar constructores de serialización](../code-quality/ca2229-implement-serialization-constructors.md)

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, agregue los constructores que faltan a la excepción y asegúrese de que tienen la accesibilidad correcta.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla cuando se produce la infracción mediante el uso de un nivel de acceso diferente para los constructores públicos.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente contiene un tipo de excepción que infringe esta regla y un tipo de excepción que se haya implementado correctamente.

 [!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../code-quality/codesnippet/CSharp/ca1032-implement-standard-exception-constructors_1.cs)]