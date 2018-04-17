---
title: 'CA1719: Los nombres de parámetro no deberían coincidir con los nombres de miembro | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- ParameterNamesShouldNotMatchMemberNames
- CA1719
helpviewer_keywords:
- CA1719
- ParameterNamesShouldNotMatchMemberNames
ms.assetid: c6fea690-1659-4ee7-a1c5-125ad6754525
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 402744debf3ad94ff303a5d27a39b67d41faa341
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ca1719-parameter-names-should-not-match-member-names"></a>CA1719: Los nombres de parámetro no deberían coincidir con los nombres de miembro
|||  
|-|-|  
|TypeName|ParameterNamesShouldNotMatchMemberNames|  
|Identificador de comprobación|CA1719|  
|Categoría|Microsoft.Naming|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 Coincide con el nombre de un miembro visible externamente, en una comparación entre mayúsculas y minúsculas, el nombre de uno de sus parámetros.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Un nombre de parámetro debe comunicar el significado del parámetro y un nombre de miembro debe comunicar el significado del miembro. Sería un diseño extraño si éstos fueran los mismos. Denominar un parámetro igual que el nombre del miembro no es intuitivo y dificulta el uso de la biblioteca.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Seleccione un nombre de parámetro que no coincide con el nombre de miembro.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Caso de desarrollos nuevos, no existe constancia escenarios se producen donde debe suprimir una advertencia de esta regla. Para enviar las bibliotecas, es posible que deba suprimir una advertencia de esta regla.  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [CA1709: Los identificadores deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: Los identificadores se deberían diferenciar en algo más que en el uso de mayúsculas y minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
 [CA1707: Los identificadores no deberían contener subrayado](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)