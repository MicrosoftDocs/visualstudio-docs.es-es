---
title: 'CA1724: Los nombres de tipo no deben coincidir con los espacios de nombres'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
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
ms.openlocfilehash: c178558743ca69fb3b62eccaf8164e4b49167ad3
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547573"
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

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 Para el desarrollo nuevo, no conocidos se producen escenarios donde se debe suprimir una advertencia de esta regla. Antes de suprimir la advertencia, considere cuidadosamente cómo se podrían confundir a los usuarios de la biblioteca por el nombre coincidente. Para enviar las bibliotecas, es posible que deba suprimir una advertencia de esta regla.