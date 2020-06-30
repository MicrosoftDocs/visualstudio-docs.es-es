---
title: 'CA1032: implementar constructores de excepción estándar | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 61b0157200ddff4cb8335118b30832a0c8950f65
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85542290"
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032: Implementar constructores de excepción estándar
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|ImplementStandardExceptionConstructors|
|Identificador de comprobación|CA1032|
|Category|Microsoft. Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
 Un tipo extiende <xref:System.Exception?displayProperty=fullName> y no declara todos los constructores necesarios.

## <a name="rule-description"></a>Descripción de la regla
 Los tipos de excepción deben implementar los siguientes constructores:

- Public NewException ()

- Public NewException (String)

- Public NewException (cadena, excepción)

- NewException protegido o privado (SerializationInfo, StreamingContext)

  El error al proporcionar el conjunto completo de constructores puede dificultar el control correcto de las excepciones. Por ejemplo, el constructor que tiene la firma `NewException(string, Exception)` se usa para crear excepciones provocadas por otras excepciones. Sin este constructor, no se puede crear y producir una instancia de la excepción personalizada que contiene una excepción interna (anidada), que es lo que debe hacer el código administrado en esta situación. Los tres primeros constructores de excepción son públicos por Convención. El cuarto constructor está protegido en clases no selladas y privado en clases selladas. Para obtener más información, vea [CA2229: implementar constructores de serialización.](../code-quality/ca2229-implement-serialization-constructors.md)

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, agregue los constructores que faltan a la excepción y asegúrese de que tienen la accesibilidad correcta.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla cuando se produce la infracción mediante el uso de un nivel de acceso diferente para los constructores públicos.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente contiene un tipo de excepción que infringe esta regla y un tipo de excepción que se ha implementado correctamente.

 [!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionMultipleCtors/cs/FxCop.Design.ExceptionMultipleCtors.cs#1)]
