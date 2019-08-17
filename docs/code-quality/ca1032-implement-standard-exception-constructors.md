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
ms.openlocfilehash: 4b294b267aa7bb1a2912ed42807ac0f878c87838
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547657"
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032: Implementar constructores de excepción estándar

|||
|-|-|
|TypeName|ImplementStandardExceptionConstructors|
|Identificador de comprobación|CA1032|
|Categoría|Microsoft.Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa

Un tipo extiende <xref:System.Exception?displayProperty=fullName> pero no declara todos los constructores necesarios.

## <a name="rule-description"></a>Descripción de la regla

Los tipos de excepción deben implementar los tres constructores siguientes:

- Public NewException ()

- Public NewException (String)

- Public NewException (cadena, excepción)

Además, si ejecuta el análisis de FxCop heredado en lugar de los [analizadores de FxCop basados en .net Compiler Platform](../code-quality/roslyn-analyzers-overview.md), la ausencia de un cuarto constructor también genera una infracción:

- NewException protegido o privado (SerializationInfo, StreamingContext)

El error al proporcionar el conjunto completo de constructores puede dificultar el control correcto de las excepciones. Por ejemplo, el constructor que tiene la firma `NewException(string, Exception)` se usa para crear excepciones provocadas por otras excepciones. Sin este constructor, no se puede crear y producir una instancia de la excepción personalizada que contiene una excepción interna (anidada), que es lo que debe hacer el código administrado en esta situación.

Los tres primeros constructores de excepción son públicos por Convención. El cuarto constructor está protegido en clases no selladas y privado en clases selladas. Para obtener más información, [vea CA2229: Implementar constructores](../code-quality/ca2229-implement-serialization-constructors.md)de serialización.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, agregue los constructores que faltan a la excepción y asegúrese de que tienen la accesibilidad correcta.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Es seguro suprimir una advertencia de esta regla cuando se produce la infracción mediante el uso de un nivel de acceso diferente para los constructores públicos. Además, es correcto suprimir la advertencia `NewException(SerializationInfo, StreamingContext)` del constructor si está creando una biblioteca de clases portable (PCL).

## <a name="example"></a>Ejemplo

El ejemplo siguiente contiene un tipo de excepción que infringe esta regla y un tipo de excepción que se ha implementado correctamente.

[!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../code-quality/codesnippet/CSharp/ca1032-implement-standard-exception-constructors_1.cs)]

## <a name="see-also"></a>Vea también

[CA2229: implementar constructores de serialización](../code-quality/ca2229-implement-serialization-constructors.md)