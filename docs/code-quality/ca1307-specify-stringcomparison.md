---
title: "CA1307: Especificar StringComparison | Microsoft Docs"
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
  - "CA1307"
  - "SpecifyStringComparison"
helpviewer_keywords: 
  - "CA1307"
  - "SpecifyStringComparison"
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1307: Especificar StringComparison
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SpecifyStringComparison|  
|Identificador de comprobación|CA1307|  
|Categoría|Microsoft.Globalization|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Una operación de comparación de cadenas utiliza una sobrecarga de método que no establece un parámetro <xref:System.StringComparison>.  
  
## Descripción de la regla  
 Muchas operaciones de cadenas y, lo que es más importante, los métodos <xref:System.String.Compare%2A> y <xref:System.String.Equals%2A>, proporcionan una sobrecarga que acepta un valor de enumeración <xref:System.StringComparison> como parámetro.  
  
 Siempre que exista una sobrecarga que tome un parámetro <xref:System.StringComparison>, debe utilizarse en lugar de una sobrecarga que no tome este parámetro.  Si establece explícitamente este parámetro, su código resultará más claro y más fácil de mantener.  
  
## Cómo corregir infracciones  
 Para corregir una infracción a esta regla, cambie los métodos de comparación de cadenas por sobrecargas que acepten la enumeración <xref:System.StringComparison> como parámetro.  Por ejemplo, cambie `String.Compare(str1, str2)` por `String.Compare(str1, str2, StringComparison.Ordinal)`.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla cuando la biblioteca o la aplicación se ha diseñado para una audiencia local limitada y, por tanto, no se va a localizar.  
  
## Vea también  
 [Advertencias de globalización](../code-quality/globalization-warnings.md)   
 [CA1309: Utilizar StringComparison ordinal](../code-quality/ca1309-use-ordinal-stringcomparison.md)