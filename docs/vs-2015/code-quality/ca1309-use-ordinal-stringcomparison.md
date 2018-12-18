---
title: 'CA1309: Utilizar StringComparison ordinal | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- UseOrdinalStringComparison
- CA1309
helpviewer_keywords:
- UseOrdinalStringComparison
- CA1309
ms.assetid: 19be0854-cb6e-4efd-a4c8-a5c1fc6f7a71
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a239d8c40a07e92ee46c2d27bf3276e9b8bba2ca
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49885035"
---
# <a name="ca1309-use-ordinal-stringcomparison"></a>CA1309: Utilizar StringComparison ordinal
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseOrdinalStringComparison|
|Identificador de comprobación|CA1309|
|Categoría|Microsoft.Globalization|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Una operación de comparación de cadenas que lingüística no establece la <xref:System.StringComparison> parámetro a **Ordinal** o **OrdinalIgnoreCase**.

## <a name="rule-description"></a>Descripción de la regla
 Muchas operaciones de cadenas, más importante la <xref:System.String.Compare%2A?displayProperty=fullName> y <xref:System.String.Equals%2A?displayProperty=fullName> métodos, ahora proporcionan una sobrecarga que acepta un <xref:System.StringComparison?displayProperty=fullName> valor de enumeración como un parámetro.

 Al especificar **StringComparison.Ordinal** o **StringComparison.OrdinalIgnoreCase**, la comparación de cadenas será lingüística. Es decir, se omiten las características que son específicas del lenguaje natural cuando se toman decisiones de comparación. Esto significa que las decisiones se basan en simples comparaciones de bytes y omitir mayúsculas y minúsculas o tablas de equivalencia parametrizadas por referencia cultural. Como resultado, si se establece explícitamente el parámetro como el **StringComparison.Ordinal** o **StringComparison.OrdinalIgnoreCase**, el código a menudo gana en velocidad, aumenta la exactitud y se convierte en más confiable.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie el método de comparación de cadenas a una sobrecarga que acepta el <xref:System.StringComparison?displayProperty=fullName> enumeración como un parámetro y especifique **Ordinal** o **OrdinalIgnoreCase**. Por ejemplo, cambie `String.Compare(str1, str2)` a `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla cuando la biblioteca o la aplicación está pensada para un público local limitado o cuándo debe usarse la semántica de la referencia cultural actual.

## <a name="see-also"></a>Vea también
 [Advertencias de globalización](../code-quality/globalization-warnings.md) [CA1307: Especificar StringComparison](../code-quality/ca1307-specify-stringcomparison.md)



