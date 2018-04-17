---
title: 'CA1724: Los nombres de tipo no deberían coincidir con los espacios de nombres | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
helpviewer_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 39e6b539d0259f83475e3e3a685bed7ffe6a7c87
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
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