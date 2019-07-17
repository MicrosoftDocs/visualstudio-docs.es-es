---
title: 'CA1306: Establecer configuración regional para tipos de datos | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1306
- SetLocaleForDataTypes
helpviewer_keywords:
- CA1306
- SetLocaleForDataTypes
ms.assetid: 104297b2-5806-4de0-a8d9-c589380a796c
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 75e67cdd058939837441bd969ac8629a6fc65dcc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200362"
---
# <a name="ca1306-set-locale-for-data-types"></a>CA1306: Establecer configuración regional de tipos de datos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SetLocaleForDataTypes|
|Identificador de comprobación|CA1306|
|Categoría|Microsoft.Globalization|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
 Un método o constructor crea uno o varios <xref:System.Data.DataTable?displayProperty=fullName> o <xref:System.Data.DataSet?displayProperty=fullName> instancias y no estableció explícitamente la propiedad de configuración regional (<xref:System.Data.DataTable.Locale%2A?displayProperty=fullName> o <xref:System.Data.DataSet.Locale%2A?displayProperty=fullName>).

## <a name="rule-description"></a>Descripción de la regla
 La configuración regional determina los elementos de presentación específicos de la referencia cultural para los datos, como el formato para valores numéricos, símbolos de divisa y criterio de ordenación. Cuando creas un <xref:System.Data.DataTable> o <xref:System.Data.DataSet>, debe establecer explícitamente la configuración regional. De forma predeterminada, la configuración regional para estos tipos es la referencia cultural actual. Para los datos que se almacenan en un archivo o base de datos y se comparten de forma global, normalmente se debe establecer la configuración regional en la referencia cultural (<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>). Cuando los datos se comparten entre referencias culturales, utilizando la configuración regional predeterminada puede hacer que el contenido de la <xref:System.Data.DataTable> o <xref:System.Data.DataSet> se presente o interpretará incorrectamente.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, establezca explícitamente la configuración regional para la <xref:System.Data.DataTable> o <xref:System.Data.DataSet>.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla cuando la biblioteca o la aplicación es para un público limitado local, no se comparten los datos o la configuración predeterminada produce el comportamiento deseado en todos los escenarios admitidos.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se crean dos <xref:System.Data.DataTable> instancias.

 [!code-csharp[FxCop.Globalization.DataTable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DataTable/cs/FxCop.Globalization.DataTable.cs#1)]

## <a name="see-also"></a>Vea también
 <xref:System.Data.DataTable?displayProperty=fullName> <xref:System.Data.DataSet?displayProperty=fullName>
 <xref:System.Globalization.CultureInfo?displayProperty=fullName>
 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>
 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>
