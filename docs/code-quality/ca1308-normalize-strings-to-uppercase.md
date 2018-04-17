---
title: 'CA1308: Normalizar las cadenas en mayúsculas | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1308
- NormalizeStringsToUppercase
helpviewer_keywords:
- NormalizeStringsToUppercase
- CA1308
ms.assetid: 7e9a7457-3f93-4938-ac6f-1389fba8d9cc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 979b6d0bbd14d6432ea376622ce61f6329f708fa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
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