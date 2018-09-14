---
title: 'CA1820: Comprobar si las cadenas están vacías mediante la longitud de cadena'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
helpviewer_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
ms.assetid: da1e70c8-b1dc-46b9-8b8f-4e6e48339681
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 24850c61216354f7d9fa197dc7c4317105ab98ba
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551423"
---
# <a name="ca1820-test-for-empty-strings-using-string-length"></a>CA1820: Comprobar si las cadenas están vacías mediante la longitud de cadena
|||
|-|-|
|TypeName|TestForEmptyStringsUsingStringLength|
|Identificador de comprobación|CA1820|
|Categoría|Microsoft.Performance|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Una cadena se compara con la cadena vacía mediante el uso de <xref:System.Object.Equals%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Descripción de la regla
 Comparación de cadenas mediante la <xref:System.String.Length%2A?displayProperty=fullName> propiedad o el <xref:System.String.IsNullOrEmpty%2A?displayProperty=fullName> método es significativamente más rápido que utilizar <xref:System.Object.Equals%2A>. Esto es porque <xref:System.Object.Equals%2A> ejecuta significativamente más instrucciones de MSIL que cualquiera de ellos <xref:System.String.IsNullOrEmpty%2A> o el número de instrucciones que se ejecuta para recuperar el <xref:System.String.Length%2A> propiedad de valor y compararlo con cero.

 Debe tener en cuenta que <xref:System.Object.Equals%2A> y <xref:System.String.Length%2A> == 0 se comportan de manera diferente en cadenas nulas. Si se intenta obtener el valor de la <xref:System.String.Length%2A> propiedad en una cadena nula, common language runtime produce una <xref:System.NullReferenceException?displayProperty=fullName>. Si realiza una comparación entre una cadena nula y una cadena vacía, common language runtime no produce una excepción; la comparación devuelve `false`. Comprobación de null no afecta significativamente el rendimiento relativo de estos dos enfoques. Cuando el destino es [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], utilice el <xref:System.String.IsNullOrEmpty%2A> método. En caso contrario, use el <xref:System.String.Length%2A> == comparación siempre que sea posible.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie la comparación para que use el <xref:System.String.Length%2A> propiedad y prueba para la cadena nula. Si el destino es [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], utilice el <xref:System.String.IsNullOrEmpty%2A> método.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si el rendimiento no es un problema.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra las distintas técnicas que se usan para buscar una cadena vacía.

 [!code-csharp[FxCop.Performance.StringTest#1](../code-quality/codesnippet/CSharp/ca1820-test-for-empty-strings-using-string-length_1.cs)]