---
title: 'CA1820: Comprobar si las cadenas están vacías mediante la longitud de cadena'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b197cacc764f1f5472d3eb074ac89199db508408
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233431"
---
# <a name="ca1820-test-for-empty-strings-using-string-length"></a>CA1820: Comprobar si las cadenas están vacías mediante la longitud de cadena

|||
|-|-|
|TypeName|TestForEmptyStringsUsingStringLength|
|Identificador de comprobación|CA1820|
|Categoría|Microsoft.Performance|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo

Una cadena se compara con la cadena <xref:System.Object.Equals%2A?displayProperty=nameWithType>vacía mediante.

## <a name="rule-description"></a>Descripción de la regla

Comparar cadenas mediante la <xref:System.String.Length%2A?displayProperty=nameWithType> propiedad o el <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> método es más rápido que utilizar <xref:System.Object.Equals%2A>. Esto se debe <xref:System.Object.Equals%2A> <xref:System.String.IsNullOrEmpty%2A> a que ejecuta mucho más instrucciones MSIL que o el número de instrucciones ejecutadas para recuperar <xref:System.String.Length%2A> el valor de propiedad y compararlo con cero.

Para cadenas <xref:System.Object.Equals%2A> nulas y `<string>.Length == 0` se comportan de manera diferente. Si intenta obtener el valor de la <xref:System.String.Length%2A> propiedad en una cadena nula, el Common Language Runtime produce una <xref:System.NullReferenceException?displayProperty=fullName>excepción. Si realiza una comparación entre una cadena nula y una cadena vacía, el Common Language Runtime no inicia una excepción y devuelve `false`. La comprobación de NULL no afecta significativamente al rendimiento relativo de estos dos enfoques. Cuando el destino sea .NET Framework 2,0 o una versión posterior <xref:System.String.IsNullOrEmpty%2A> , use el método. De lo contrario, <xref:System.String.Length%2A> use la comparación = = 0 siempre que sea posible.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, cambie la comparación para que <xref:System.String.IsNullOrEmpty%2A> use el método.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Es seguro suprimir una advertencia de esta regla si el rendimiento no es un problema.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestran las distintas técnicas que se usan para buscar una cadena vacía.

[!code-csharp[FxCop.Performance.StringTest#1](../code-quality/codesnippet/CSharp/ca1820-test-for-empty-strings-using-string-length_1.cs)]