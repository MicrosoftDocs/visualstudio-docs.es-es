---
title: "CA1306: Establecer configuraci&#243;n regional para tipos de datos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1306"
  - "SetLocaleForDataTypes"
helpviewer_keywords: 
  - "CA1306"
  - "SetLocaleForDataTypes"
ms.assetid: 104297b2-5806-4de0-a8d9-c589380a796c
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1306: Establecer configuraci&#243;n regional para tipos de datos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SetLocaleForDataTypes|  
|Identificador de comprobación|CA1306|  
|Categoría|Microsoft.Globalization|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Un método o constructor creó una o más instancias de <xref:System.Data.DataTable?displayProperty=fullName> o <xref:System.Data.DataSet?displayProperty=fullName> y no estableció explícitamente la propiedad de configuración regional \(<xref:System.Data.DataTable.Locale%2A?displayProperty=fullName> o <xref:System.Data.DataSet.Locale%2A?displayProperty=fullName>\).  
  
## Descripción de la regla  
 La configuración regional determina los elementos de presentación específicos de la referencia cultural para los datos, como el formato para los valores numéricos, símbolos de moneda y criterio de ordenación.  Cuando se crea <xref:System.Data.DataTable> o <xref:System.Data.DataSet> debe establecerse explícitamente la configuración regional.  De forma predeterminada, la configuración regional para estos tipos es la referencia cultural actual.  Para los datos almacenados en un archivo o una base de datos y se comparte de forma global, la configuración regional debe establecerse normalmente en la referencia cultural invariable \(<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>\).  Cuando las referencias culturales comparten datos, el hecho de utilizar la configuración regional puede provocar que el contenido de <xref:System.Data.DataTable> o <xref:System.Data.DataSet> se presente o se interprete incorrectamente.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, establezca explícitamente la configuración regional para <xref:System.Data.DataTable> o <xref:System.Data.DataSet>.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla cuando la biblioteca o la aplicación sea para un público local limitado, los datos no estén compartidos o la configuración predeterminada produzca el comportamiento deseado en todos los escenarios compatibles.  
  
## Ejemplo  
 El ejemplo siguiente crea dos instancias de <xref:System.Data.DataTable>.  
  
 [!code-cs[FxCop.Globalization.DataTable#1](../code-quality/codesnippet/CSharp/ca1306-set-locale-for-data-types_1.cs)]  
  
## Vea también  
 <xref:System.Data.DataTable?displayProperty=fullName>   
 <xref:System.Data.DataSet?displayProperty=fullName>   
 <xref:System.Globalization.CultureInfo?displayProperty=fullName>   
 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>   
 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>