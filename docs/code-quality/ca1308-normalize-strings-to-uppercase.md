---
title: "CA1308: Normalizar las cadenas en mayúsculas | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1308
- NormalizeStringsToUppercase
helpviewer_keywords:
- NormalizeStringsToUppercase
- CA1308
ms.assetid: 7e9a7457-3f93-4938-ac6f-1389fba8d9cc
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9064ca9861f609499971b9f5188f5b0006458c15
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="ca1308-normalize-strings-to-uppercase"></a>CA1308: Normalizar las cadenas en mayúsculas
|||  
|-|-|  
|TypeName|NormalizeStringsToUppercase|  
|Identificador de comprobación|CA1308|  
|Categoría|Microsoft.Globalization|  
|Cambio problemático|Poco problemático|  
  
## <a name="cause"></a>Motivo  
 Una operación normaliza una cadena a minúsculas.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Las cadenas se deberían normalizar para que se escriban en letras mayúsculas. Un grupo pequeño de caracteres, al que se convierten a minúsculas, no puede realizar un de ida y vuelta. Para realizar un viaje de ida y medios para convertir los caracteres de una configuración regional para otra configuración regional que representa datos de caracteres de forma diferente y, a continuación, con precisión recuperan los caracteres originales de los caracteres convertidos.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Cambiar las operaciones que las cadenas se convierten a minúsculas para que las cadenas se convierten a mayúsculas en su lugar. Por ejemplo, cambie `String.ToLower(CultureInfo.InvariantCulture)` a `String.ToUpper(CultureInfo.InvariantCulture)`.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Es seguro suprimir un mensaje de advertencia cuando no esté tomando una decisión de seguridad en función del resultado (por ejemplo, al que se están mostrando en la interfaz de usuario).  
  
## <a name="see-also"></a>Vea también  
 [Advertencias de globalización](../code-quality/globalization-warnings.md)