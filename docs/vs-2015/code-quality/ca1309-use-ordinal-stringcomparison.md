---
title: 'CA1309: usar StringComparison ordinal | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseOrdinalStringComparison
- CA1309
helpviewer_keywords:
- UseOrdinalStringComparison
- CA1309
ms.assetid: 19be0854-cb6e-4efd-a4c8-a5c1fc6f7a71
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: be60d2a1dcb769a0b7a8574984de3d288bf57af4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538884"
---
# <a name="ca1309-use-ordinal-stringcomparison"></a>CA1309: Utilizar StringComparison ordinal
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|UseOrdinalStringComparison|
|Identificador de comprobación|CA1309|
|Category|Microsoft. Globalization|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
 Una operación de comparación de cadenas que no sea lingüística no establece el <xref:System.StringComparison> parámetro en **ordinal** o en **OrdinalIgnoreCase**.

## <a name="rule-description"></a>Descripción de la regla
 Muchas operaciones de cadena, más importantes <xref:System.String.Compare%2A?displayProperty=fullName> los <xref:System.String.Equals%2A?displayProperty=fullName> métodos y, ahora proporcionan una sobrecarga que acepta un <xref:System.StringComparison?displayProperty=fullName> valor de enumeración como parámetro.

 Al especificar **StringComparison. ordinal** o **StringComparison. OrdinalIgnoreCase**, la comparación de cadenas no será lingüística. Es decir, las características que son específicas del lenguaje natural se omiten cuando se toman decisiones de comparación. Esto significa que las decisiones se basan en comparaciones de bytes simples y omiten las tablas de mayúsculas y minúsculas o de equivalencia parametrizadas por referencia cultural. Como resultado, al establecer explícitamente el parámetro en **StringComparison. ordinal** o **StringComparison. OrdinalIgnoreCase**, el código a menudo gana velocidad, aumenta la exactitud y se vuelve más confiable.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie el método de comparación de cadenas a una sobrecarga que acepte la <xref:System.StringComparison?displayProperty=fullName> enumeración como parámetro y especifique **ordinal** o **OrdinalIgnoreCase**. Por ejemplo, cambie `String.Compare(str1, str2)` a `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla cuando la biblioteca o aplicación está pensada para un público local limitado o cuando se debe usar la semántica de la referencia cultural actual.

## <a name="see-also"></a>Consulte también
 [Advertencias de globalización](../code-quality/globalization-warnings.md) [CA1307: especificar StringComparison](../code-quality/ca1307-specify-stringcomparison.md)
