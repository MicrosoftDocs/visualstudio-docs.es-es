---
title: 'CA1719: Los nombres de parámetro no deberían coincidir con los nombres de miembro | Microsoft Docs'
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
- ParameterNamesShouldNotMatchMemberNames
- CA1719
helpviewer_keywords:
- CA1719
- ParameterNamesShouldNotMatchMemberNames
ms.assetid: c6fea690-1659-4ee7-a1c5-125ad6754525
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 13a6326391e543ef8220725ae982b8cfa75abb1b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49216711"
---
# <a name="ca1719-parameter-names-should-not-match-member-names"></a>CA1719: Los nombres de parámetro no deberían coincidir con los nombres de miembro
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
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
 Seleccione un nombre de parámetro que no coincide con el nombre del miembro.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Para el desarrollo nuevo, no conocidos se producen escenarios donde se debe suprimir una advertencia de esta regla. Para enviar las bibliotecas, es posible que deba suprimir una advertencia de esta regla.

## <a name="related-rules"></a>Reglas relacionadas
 [CA1709: Los identificadores deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Los identificadores se deberían diferenciar en algo más que en el uso de mayúsculas y minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707: Los identificadores no deberían contener subrayado](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)



