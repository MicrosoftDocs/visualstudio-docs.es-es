---
title: "CA1724: Los nombres de tipo no deberían coincidir con los espacios de nombres | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
helpviewer_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 556fd9eee1bc453d4f9782459050367e18a3193b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724: Los nombres de tipo no deben coincidir con los espacios de nombres
|||  
|-|-|  
|TypeName|TypeNamesShouldNotMatchNamespaces|  
|Identificador de comprobación|CA1724|  
|Categoría|Microsoft.Naming|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 Un nombre de tipo coincide con un [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] espacios de nombres en una comparación entre mayúsculas y minúsculas.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Los nombres de tipo no deben coincidir con los nombres de espacios de nombres definidos en la biblioteca de clases de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Infringir esta regla puede reducir la utilidad de la biblioteca.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Seleccione un nombre de tipo que no coincide con el nombre de un [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] espacio de nombres de biblioteca de clases.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Caso de desarrollos nuevos, no existe constancia escenarios se producen donde debe suprimir una advertencia de esta regla. Antes de suprimir la advertencia, considere cuidadosamente cómo los usuarios de la biblioteca pueden confundir con el nombre coincidente. Para enviar las bibliotecas, es posible que deba suprimir una advertencia de esta regla.