---
title: 'CA1307: Especificar StringComparison | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1307
- SpecifyStringComparison
helpviewer_keywords:
- CA1307
- SpecifyStringComparison
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 61d8ca557bfc55e3488a35e82f0242f931c51ed4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307: Especificar StringComparison
|||  
|-|-|  
|TypeName|SpecifyStringComparison|  
|Identificador de comprobación|CA1307|  
|Categoría|Microsoft.Globalization|  
|Cambio problemático|Poco problemático|  
  
## <a name="cause"></a>Motivo  
 Una operación de comparación de cadenas utiliza una sobrecarga del método que no establece un <xref:System.StringComparison> parámetro.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Muchas operaciones de cadenas, más importante la <xref:System.String.Compare%2A> y <xref:System.String.Equals%2A> métodos, proporcionan una sobrecarga que acepta un <xref:System.StringComparison> valor de enumeración como parámetro.  
  
 Cada vez que existe una sobrecarga que toma un <xref:System.StringComparison> parámetro, se debería utilizar en lugar de una sobrecarga que no tome este parámetro. Si este parámetro se establece explícitamente, el código es a menudo más clara realizadas y fáciles de mantener.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, cambiar los métodos de comparación de cadenas por sobrecargas que acepten la <xref:System.StringComparison> enumeración como parámetro. Por ejemplo: cambiar `String.Compare(str1, str2)` a `String.Compare(str1, str2, StringComparison.Ordinal)`.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla cuando la biblioteca o la aplicación está destinada a una audiencia local limitada y, por tanto, no será localizada.  
  
## <a name="see-also"></a>Vea también  
 [Advertencias de globalización](../code-quality/globalization-warnings.md)   
 [CA1309: Utilizar StringComparison ordinal](../code-quality/ca1309-use-ordinal-stringcomparison.md)