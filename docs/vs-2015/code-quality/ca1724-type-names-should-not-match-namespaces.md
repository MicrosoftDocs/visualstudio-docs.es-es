---
title: 'CA1724: Los nombres de tipo no deberían coincidir con los espacios de nombres | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
helpviewer_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5331a32db054b1cb3939bbfd3ba088ab5da33f96
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49903184"
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724: Los nombres de tipo no deben coincidir con los espacios de nombres
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypeNamesShouldNotMatchNamespaces|
|Identificador de comprobación|CA1724|
|Categoría|Microsoft.Naming|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un nombre de tipo coincide con un [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] espacios de nombres en una comparación entre mayúsculas y minúsculas.

## <a name="rule-description"></a>Descripción de la regla
 Los nombres de tipo no deben coincidir con los nombres de espacios de nombres definidos en la biblioteca de clases de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Infringir esta regla puede reducir la utilidad de la biblioteca.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Seleccione un nombre de tipo que no coincide con el nombre de un [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] espacio de nombres de biblioteca de clases.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Para el desarrollo nuevo, no conocidos se producen escenarios donde se debe suprimir una advertencia de esta regla. Antes de suprimir la advertencia, considere cuidadosamente cómo se podrían confundir a los usuarios de la biblioteca por el nombre coincidente. Para enviar las bibliotecas, es posible que deba suprimir una advertencia de esta regla.



