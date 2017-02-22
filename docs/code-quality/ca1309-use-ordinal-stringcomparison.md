---
title: "CA1309: Utilizar StringComparison ordinal | Microsoft Docs"
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
  - "UseOrdinalStringComparison"
  - "CA1309"
helpviewer_keywords: 
  - "UseOrdinalStringComparison"
  - "CA1309"
ms.assetid: 19be0854-cb6e-4efd-a4c8-a5c1fc6f7a71
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1309: Utilizar StringComparison ordinal
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseOrdinalStringComparison|  
|Identificador de comprobación|CA1309|  
|Categoría|Microsoft.Globalization|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Una operación no lingüística de comparación de cadenas no establece el parámetro <xref:System.StringComparison> en **Ordinal** ni en **OrdinalIgnoreCase**.  
  
## Descripción de la regla  
 Muchas operaciones de cadenas y, lo que es más importante, los métodos <xref:System.String.Compare%2A?displayProperty=fullName> y <xref:System.String.Equals%2A?displayProperty=fullName>, proporcionan ahora una sobrecarga que acepta un valor de enumeración <xref:System.StringComparision?displayProperty=fullName> como parámetro.  
  
 Si especifica **StringComparison.Ordinal** o **StringComparison.OrdinalIgnoreCase**, la comparación de cadenas será no lingüística.  Es decir, al tomar decisiones de comparación, se omiten las características específicas del lenguaje natural.  Esto significa que las decisiones se basan en comparaciones de bytes simples y no distinguen entre mayúsculas y minúsculas, u omiten las tablas de equivalencia que están parametrizadas por referencia cultural.  Por tanto, si establece explícitamente el parámetro en **StringComparison.Ordinal** o **StringComparison.OrdinalIgnoreCase**, su código será más rápido, más exacto y más confiable.  
  
## Cómo corregir infracciones  
 Para corregir una infracción a esta regla, cambie el método de comparación de cadenas por una sobrecarga que acepte la enumeración <xref:System.StringComparison?displayProperty=fullName> como parámetro, y especifique **Ordinal** u **OrdinalIgnoreCase**.  Por ejemplo, cambie `String.Compare(str1, str2)` a `String.Compare(str1, str2, StringComparison.Ordinal)`.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla cuando la biblioteca o la aplicación está diseñada para una audiencia local limitada o cuando se debe utilizar las semántica de la referencia cultural actual.  
  
## Vea también  
 [Advertencias de globalización](../code-quality/globalization-warnings.md)   
 [CA1307: Especificar StringComparison](../code-quality/ca1307-specify-stringcomparison.md)