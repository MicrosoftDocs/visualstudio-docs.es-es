---
title: 'CA1307: Especificar StringComparison | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1307
- SpecifyStringComparison
helpviewer_keywords:
- CA1307
- SpecifyStringComparison
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 292e174feeb123c640306bc8ef3ffedd7e8847f6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200355"
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307: Especificar StringComparison
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SpecifyStringComparison|
|Identificador de comprobación|CA1307|
|Categoría|Microsoft.Globalization|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
 Una operación de comparación de cadenas utiliza una sobrecarga del método que no ha establecido un <xref:System.StringComparison> parámetro.

## <a name="rule-description"></a>Descripción de la regla
 Muchas operaciones de cadenas, más importante la <xref:System.String.Compare%2A> y <xref:System.String.Equals%2A> métodos, proporcionar una sobrecarga que acepta un <xref:System.StringComparison> valor de enumeración como un parámetro.

 Cada vez que existe una sobrecarga que toma un <xref:System.StringComparison> parámetro, se debe usar en lugar de una sobrecarga que no tome este parámetro. Si este parámetro se establece explícitamente, el código suele ser realizadas sea más clara y fácil de mantener.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambiar los métodos de comparación de cadenas a las sobrecargas que aceptan el <xref:System.StringComparison> enumeración como un parámetro. Por ejemplo: cambiar `String.Compare(str1, str2)` a `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla cuando la biblioteca o la aplicación está destinada a una audiencia local limitada y, por tanto, no estará localizada.

## <a name="see-also"></a>Vea también
 [Advertencias de globalización](../code-quality/globalization-warnings.md) [CA1309: Utilizar StringComparison ordinal](../code-quality/ca1309-use-ordinal-stringcomparison.md)
