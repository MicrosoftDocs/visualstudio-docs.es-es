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
ms.openlocfilehash: 2c528266c54bbb2f3f0d9420461d700a46b09bd5
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922279"
---
# <a name="ca1309-use-ordinal-stringcomparison"></a>CA1309: Utilizar StringComparison ordinal

|||
|-|-|
|TypeName|UseOrdinalStringComparison|
|Identificador de comprobación|CA1309|
|Categoría|Microsoft. Globalization|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa

Una operación de comparación de cadenas que no sea lingüística no establece <xref:System.StringComparison> el parámetro en **ordinal** o en **OrdinalIgnoreCase**.

## <a name="rule-description"></a>Descripción de la regla
Muchas operaciones de cadena, lo que es <xref:System.String.Compare%2A?displayProperty=fullName> más <xref:System.String.Equals%2A?displayProperty=fullName> importante, los métodos y, ahora proporcionan una <xref:System.StringComparison?displayProperty=fullName> sobrecarga que acepta un valor de enumeración como parámetro.

Al especificar **StringComparison. ordinal** o **StringComparison. OrdinalIgnoreCase**, la comparación de cadenas no es lingüística. Es decir, las características que son específicas del lenguaje natural se omiten cuando se toman decisiones de comparación. Omitir las características del lenguaje natural significa que las decisiones se basan en comparaciones de bytes simples y no en tablas de equivalencia de mayúsculas y minúsculas que se parametrizan por referencia cultural. Como resultado, al establecer explícitamente el parámetro en **StringComparison. ordinal** o **StringComparison. OrdinalIgnoreCase**, el código a menudo gana velocidad, aumenta la exactitud y se vuelve más confiable.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, cambie el método de comparación de cadenas a una sobrecarga <xref:System.StringComparison?displayProperty=fullName> que acepte la enumeración como parámetro y especifique **ordinal** o **OrdinalIgnoreCase**. Por ejemplo, cambie `String.Compare(str1, str2)` a `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Es seguro suprimir una advertencia de esta regla cuando la biblioteca o aplicación está pensada para un público local limitado, o cuando se debe usar la semántica de la referencia cultural actual.

## <a name="see-also"></a>Vea también

- [Advertencias de globalización](../code-quality/globalization-warnings.md)
- [CA1307: Especificar StringComparison](../code-quality/ca1307-specify-stringcomparison.md)