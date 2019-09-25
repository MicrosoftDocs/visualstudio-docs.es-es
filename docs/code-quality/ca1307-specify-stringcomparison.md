---
title: 'CA1307: Especificar StringComparison'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1307
- SpecifyStringComparison
helpviewer_keywords:
- CA1307
- SpecifyStringComparison
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e352eea1b7fcf82cb948315affeae6e30690a4aa
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234970"
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307: Especificar StringComparison

|||
|-|-|
|TypeName|SpecifyStringComparison|
|Identificador de comprobación|CA1307|
|Categoría|Microsoft. Globalization|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo
Una operación de comparación de cadenas utiliza una sobrecarga de método que no <xref:System.StringComparison> establece un parámetro.

## <a name="rule-description"></a>Descripción de la regla
Muchas operaciones de cadena, más importantes <xref:System.String.Compare%2A> los <xref:System.String.Equals%2A> métodos y, proporcionan una sobrecarga que acepta <xref:System.StringComparison> un valor de enumeración como parámetro.

Siempre que existe una sobrecarga que toma <xref:System.StringComparison> un parámetro, se debe usar en lugar de una sobrecarga que no tome este parámetro. Al establecer este parámetro explícitamente, el código suele ser más claro y más fácil de mantener.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, cambie los métodos de comparación de cadenas a las sobrecargas que aceptan la <xref:System.StringComparison> enumeración como parámetro. Por ejemplo: cambie `String.Compare(str1, str2)` a `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Es seguro suprimir una advertencia de esta regla cuando la biblioteca o aplicación está pensada para un público local limitado y, por lo tanto, no se localizará.

## <a name="see-also"></a>Vea también

- [Advertencias de globalización](../code-quality/globalization-warnings.md)
- [CA1309: Usar StringComparison ordinal](../code-quality/ca1309-use-ordinal-stringcomparison.md)