---
title: 'CA1719: los nombres de parámetro no deben coincidir con los nombres de miembro | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ParameterNamesShouldNotMatchMemberNames
- CA1719
helpviewer_keywords:
- CA1719
- ParameterNamesShouldNotMatchMemberNames
ms.assetid: c6fea690-1659-4ee7-a1c5-125ad6754525
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5024d2ddb7f31593c8eaedfc2fb421b4a0e9b0a4
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545371"
---
# <a name="ca1719-parameter-names-should-not-match-member-names"></a>CA1719: Los nombres de parámetro no deben coincidir con los nombres de miembro
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Valor|
|-|-|
|TypeName|ParameterNamesShouldNotMatchMemberNames|
|Identificador de comprobación|CA1719|
|Categoría|Microsoft.Naming|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 El nombre de un miembro visible externamente coincide con, en una comparación sin distinción entre mayúsculas y minúsculas, con el nombre de uno de sus parámetros.

## <a name="rule-description"></a>Descripción de la regla
 Un nombre de parámetro debe comunicar el significado del parámetro y un nombre de miembro debe comunicar el significado del miembro. Sería un diseño extraño si éstos fueran los mismos. Denominar un parámetro igual que el nombre del miembro no es intuitivo y dificulta el uso de la biblioteca.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Seleccione un nombre de parámetro que no coincida con el nombre del miembro.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 En el desarrollo nuevo, no se produce ningún escenario conocido en el que debe suprimir una advertencia de esta regla. En el caso de las bibliotecas de envío, es posible que tenga que suprimir una advertencia de esta regla.

## <a name="related-rules"></a>Reglas relacionadas
 [CA1709: Los identificadores deben utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Los identificadores se deben diferenciar en algo más que en el uso de mayúsculas y minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707: Los identificadores no deben contener caracteres de subrayado](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)
