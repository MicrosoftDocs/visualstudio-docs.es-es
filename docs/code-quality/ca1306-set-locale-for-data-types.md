---
title: 'CA1306: Establecer configuración regional de tipos de datos'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1306
- SetLocaleForDataTypes
helpviewer_keywords:
- CA1306
- SetLocaleForDataTypes
ms.assetid: 104297b2-5806-4de0-a8d9-c589380a796c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aa74ce81e7923115cf4fa07aba26be171e187690
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54946560"
---
# <a name="ca1306-set-locale-for-data-types"></a>CA1306: Establecer configuración regional de tipos de datos

|||
|-|-|
|TypeName|SetLocaleForDataTypes|
|Identificador de comprobación|CA1306|
|Categoría|Microsoft.Globalization|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un método o constructor crea uno o varios <xref:System.Data.DataTable?displayProperty=fullName> o <xref:System.Data.DataSet?displayProperty=fullName> instancias y no estableció explícitamente la propiedad de configuración regional (<xref:System.Data.DataTable.Locale%2A?displayProperty=fullName> o <xref:System.Data.DataSet.Locale%2A?displayProperty=fullName>).

## <a name="rule-description"></a>Descripción de la regla
 La configuración regional determina los elementos de presentación específicos de la referencia cultural para los datos, como el formato para valores numéricos, símbolos de divisa y criterio de ordenación. Cuando creas un <xref:System.Data.DataTable> o <xref:System.Data.DataSet>, debe establecer explícitamente la configuración regional. De forma predeterminada, la configuración regional para estos tipos es la referencia cultural actual. Para los datos que se almacenan en un archivo o base de datos y se comparten de forma global, normalmente se debe establecer la configuración regional en la referencia cultural (<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>). Cuando los datos se comparten entre referencias culturales, utilizando la configuración regional predeterminada puede hacer que el contenido de la <xref:System.Data.DataTable> o <xref:System.Data.DataSet> se presente o interpretará incorrectamente.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, establezca explícitamente la configuración regional para la <xref:System.Data.DataTable> o <xref:System.Data.DataSet>.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 Es seguro suprimir una advertencia de esta regla cuando la biblioteca o la aplicación es para un público limitado local, no se comparten los datos o la configuración predeterminada produce el comportamiento deseado en todos los escenarios admitidos.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se crean dos <xref:System.Data.DataTable> instancias.

 [!code-csharp[FxCop.Globalization.DataTable#1](../code-quality/codesnippet/CSharp/ca1306-set-locale-for-data-types_1.cs)]

## <a name="see-also"></a>Vea también

- <xref:System.Data.DataTable?displayProperty=fullName>
- <xref:System.Data.DataSet?displayProperty=fullName>
- <xref:System.Globalization.CultureInfo?displayProperty=fullName>
- <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>
- <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>