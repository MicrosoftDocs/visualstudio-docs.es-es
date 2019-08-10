---
title: 'CA1719: Los nombres de parámetro no deben coincidir con los nombres de miembro'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ParameterNamesShouldNotMatchMemberNames
- CA1719
helpviewer_keywords:
- CA1719
- ParameterNamesShouldNotMatchMemberNames
ms.assetid: c6fea690-1659-4ee7-a1c5-125ad6754525
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9b3e34bec0e199e1eb0b49a88517e9551b9b13cd
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921625"
---
# <a name="ca1719-parameter-names-should-not-match-member-names"></a>CA1719: Los nombres de parámetro no deben coincidir con los nombres de miembro

|||
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
[CA1709: Los identificadores deben usar mayúsculas y minúsculas correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

[CA1708: Los identificadores deben diferir más que el uso de mayúsculas y minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

[CA1707: Los identificadores no deben contener guiones bajos](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)