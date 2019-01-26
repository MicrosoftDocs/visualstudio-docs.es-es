---
title: 'CA1307: Especificar StringComparison'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 2e3896056612631bac0c871ea7b09204e2622492
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55018285"
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307: Especificar StringComparison

|||
|-|-|
|TypeName|SpecifyStringComparison|
|Identificador de comprobación|CA1307|
|Categoría|Microsoft.Globalization|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Una operación de comparación de cadenas utiliza una sobrecarga del método que no ha establecido un <xref:System.StringComparison> parámetro.

## <a name="rule-description"></a>Descripción de la regla
 Muchas operaciones de cadenas, más importante la <xref:System.String.Compare%2A> y <xref:System.String.Equals%2A> métodos, proporcionar una sobrecarga que acepta un <xref:System.StringComparison> valor de enumeración como un parámetro.

 Cada vez que existe una sobrecarga que toma un <xref:System.StringComparison> parámetro, se debe usar en lugar de una sobrecarga que no tome este parámetro. Si este parámetro se establece explícitamente, el código suele ser realizadas sea más clara y fácil de mantener.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambiar los métodos de comparación de cadenas a las sobrecargas que aceptan el <xref:System.StringComparison> enumeración como un parámetro. Por ejemplo: cambiar `String.Compare(str1, str2)` a `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 Es seguro suprimir una advertencia de esta regla cuando la biblioteca o la aplicación está destinada a una audiencia local limitada y, por tanto, no estará localizada.

## <a name="see-also"></a>Vea también

- [Advertencias de globalización](../code-quality/globalization-warnings.md)
- [CA1309: Utilizar StringComparison ordinal](../code-quality/ca1309-use-ordinal-stringcomparison.md)