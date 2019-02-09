---
title: 'CA1309: Utilizar StringComparison ordinal'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UseOrdinalStringComparison
- CA1309
helpviewer_keywords:
- UseOrdinalStringComparison
- CA1309
ms.assetid: 19be0854-cb6e-4efd-a4c8-a5c1fc6f7a71
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b00accdbdb08e4267bbca2b7e5fab8002f539f1d
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55922541"
---
# <a name="ca1309-use-ordinal-stringcomparison"></a>CA1309: Utilizar StringComparison ordinal

|||
|-|-|
|TypeName|UseOrdinalStringComparison|
|Identificador de comprobación|CA1309|
|Categoría|Microsoft.Globalization|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo

Una operación de comparación de cadenas que lingüística no establece la <xref:System.StringComparison> parámetro a **Ordinal** o **OrdinalIgnoreCase**.

## <a name="rule-description"></a>Descripción de la regla
 Muchas operaciones de cadenas y, lo más importante la <xref:System.String.Compare%2A?displayProperty=fullName> y <xref:System.String.Equals%2A?displayProperty=fullName> métodos, ahora proporcionan una sobrecarga que acepta un <xref:System.StringComparison?displayProperty=fullName> valor de enumeración como un parámetro.

 Al especificar **StringComparison.Ordinal** o **StringComparison.OrdinalIgnoreCase**, la comparación de cadenas es no lingüísticos. Es decir, se omiten las características que son específicas del lenguaje natural cuando se toman decisiones de comparación. Se omitirá las características de lenguaje natural, significa que las decisiones se basan en simples comparaciones de bytes y no en mayúsculas y minúsculas o tablas de equivalencia parametrizadas por referencia cultural. Como resultado, si se establece explícitamente el parámetro como el **StringComparison.Ordinal** o **StringComparison.OrdinalIgnoreCase**, el código a menudo gana en velocidad, aumenta la exactitud y se convierte en más confiable.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie el método de comparación de cadenas a una sobrecarga que acepta el <xref:System.StringComparison?displayProperty=fullName> enumeración como un parámetro y especifique **Ordinal** o **OrdinalIgnoreCase**. Por ejemplo, cambie `String.Compare(str1, str2)` a `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 Es seguro suprimir una advertencia de esta regla cuando la biblioteca o la aplicación está destinada a una audiencia local limitada, o cuando se debe usar la semántica de la referencia cultural actual.

## <a name="see-also"></a>Vea también

- [Advertencias de globalización](../code-quality/globalization-warnings.md)
- [CA1307: Especificar StringComparison](../code-quality/ca1307-specify-stringcomparison.md)