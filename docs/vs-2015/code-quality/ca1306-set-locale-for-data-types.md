---
title: 'CA1306: establecer configuración regional para tipos de datos | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: edd1d6a7623f96f03403883ee2585d245414bb3b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539027"
---
# <a name="ca1306-set-locale-for-data-types"></a>CA1306: Establecer configuración regional de tipos de datos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|SetLocaleForDataTypes|
|Identificador de comprobación|CA1306|
|Category|Microsoft. Globalization|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
 Un método o constructor creó una o varias <xref:System.Data.DataTable?displayProperty=fullName> instancias de o <xref:System.Data.DataSet?displayProperty=fullName> y no estableció explícitamente la propiedad de configuración regional ( <xref:System.Data.DataTable.Locale%2A?displayProperty=fullName> o <xref:System.Data.DataSet.Locale%2A?displayProperty=fullName> ).

## <a name="rule-description"></a>Descripción de la regla
 La configuración regional determina los elementos de presentación específicos de la referencia cultural para los datos, como el formato utilizado para los valores numéricos, los símbolos de moneda y el criterio de ordenación. Al crear <xref:System.Data.DataTable> o <xref:System.Data.DataSet> , debe establecer la configuración regional explícitamente. De forma predeterminada, la configuración regional de estos tipos es la referencia cultural actual. En el caso de los datos que se almacenan en una base de datos o un archivo y se comparten de forma global, la configuración regional debe establecerse normalmente en la referencia cultural de todos los idiomas ( <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName> ). Cuando los datos se comparten entre las referencias culturales, el uso de la configuración regional predeterminada puede hacer que el contenido de <xref:System.Data.DataTable> o <xref:System.Data.DataSet> se presente o se interprete de forma incorrecta.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, establezca explícitamente la configuración regional de <xref:System.Data.DataTable> o <xref:System.Data.DataSet> .

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla cuando la biblioteca o aplicación es para un público local limitado, no se comparten los datos, o la configuración predeterminada produce el comportamiento deseado en todos los escenarios admitidos.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se crean dos <xref:System.Data.DataTable> instancias de.

 [!code-csharp[FxCop.Globalization.DataTable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DataTable/cs/FxCop.Globalization.DataTable.cs#1)]

## <a name="see-also"></a>Consulte también
 <xref:System.Data.DataTable?displayProperty=fullName> <xref:System.Data.DataSet?displayProperty=fullName>
 <xref:System.Globalization.CultureInfo?displayProperty=fullName>
 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>
 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>
