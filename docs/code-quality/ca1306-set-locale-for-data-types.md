---
title: 'CA1306: Establecer configuración regional de tipos de datos'
ms.date: 11/04/2016
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
ms.openlocfilehash: aaf16ccd187681be7406fdadbde620a167a40c96
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235026"
---
# <a name="ca1306-set-locale-for-data-types"></a>CA1306: Establecer configuración regional de tipos de datos

|||
|-|-|
|TypeName|SetLocaleForDataTypes|
|Identificador de comprobación|CA1306|
|Categoría|Microsoft. Globalization|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo
Un método o constructor creó una o varias <xref:System.Data.DataTable?displayProperty=fullName> instancias <xref:System.Data.DataSet?displayProperty=fullName> de o y no estableció explícitamente la propiedad de configuración<xref:System.Data.DataTable.Locale%2A?displayProperty=fullName> regional <xref:System.Data.DataSet.Locale%2A?displayProperty=fullName>(o).

## <a name="rule-description"></a>Descripción de la regla
La configuración regional determina los elementos de presentación específicos de la referencia cultural para los datos, como el formato utilizado para los valores numéricos, los símbolos de moneda y el criterio de ordenación. Al crear <xref:System.Data.DataTable> o <xref:System.Data.DataSet>, debe establecer la configuración regional explícitamente. De forma predeterminada, la configuración regional de estos tipos es la referencia cultural actual. En el caso de los datos que se almacenan en una base de datos o un archivo y se comparten de forma global, la configuración regional debe establecerse normalmente en la referencia cultural de todos los idiomas (<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>). Cuando los datos se comparten entre las referencias culturales, el uso de la configuración regional predeterminada puede <xref:System.Data.DataTable> hacer <xref:System.Data.DataSet> que el contenido de o se presente o se interprete de forma incorrecta.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, establezca explícitamente la configuración regional <xref:System.Data.DataTable> de <xref:System.Data.DataSet>o.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Es seguro suprimir una advertencia de esta regla cuando la biblioteca o aplicación es para un público local limitado, no se comparten los datos, o la configuración predeterminada produce el comportamiento deseado en todos los escenarios admitidos.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se <xref:System.Data.DataTable> crean dos instancias de.

[!code-csharp[FxCop.Globalization.DataTable#1](../code-quality/codesnippet/CSharp/ca1306-set-locale-for-data-types_1.cs)]

## <a name="see-also"></a>Vea también

- <xref:System.Data.DataTable?displayProperty=fullName>
- <xref:System.Data.DataSet?displayProperty=fullName>
- <xref:System.Globalization.CultureInfo?displayProperty=fullName>
- <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>
- <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>