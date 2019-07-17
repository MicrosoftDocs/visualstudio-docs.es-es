---
title: 'CA1032: Implementar constructores de excepción estándar | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1032
- ImplementStandardExceptionConstructors
helpviewer_keywords:
- CA1032
- ImplementStandardExceptionConstructors
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c59da56304a5d1d8f2cca7eaf886fd5ebc37f8ef
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68205843"
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032: Implementar constructores de excepción estándar
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ImplementStandardExceptionConstructors|
|Identificador de comprobación|CA1032|
|Categoría|Microsoft.Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
 Extiende un tipo <xref:System.Exception?displayProperty=fullName> y no declara todos los constructores necesarios.

## <a name="rule-description"></a>Descripción de la regla
 Tipos de excepción deben implementar los constructores siguientes:

- NewException() pública

- NewException(string) pública

- pública NewException (string, excepción)

- Protected o private NewException (SerializationInfo, StreamingContext)

  El error al proporcionar el conjunto completo de constructores puede dificultar el control correcto de las excepciones. Por ejemplo, el constructor que tiene la firma `NewException(string, Exception)` se usa para crear las excepciones producidas por otras excepciones. Sin este constructor no puede crear y producir una instancia de la excepción personalizada que contiene una excepción interna (anidada), que es el código administrado debe hacer en esta situación. Los primeros tres constructores de excepción son públicos por convención. El cuarto constructor está protegido en clases no selladas y private en clases selladas. Para obtener más información, consulte [CA2229: implementar constructores de serialización](../code-quality/ca2229-implement-serialization-constructors.md)

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, agregue los constructores que faltan a la excepción y asegúrese de que tienen la accesibilidad correcta.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla cuando se produjo la infracción de mediante el uso de un nivel de acceso diferente para los constructores públicos.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente contiene un tipo de excepción que infringe esta regla y un tipo de excepción que se implementa correctamente.

 [!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionMultipleCtors/cs/FxCop.Design.ExceptionMultipleCtors.cs#1)]
