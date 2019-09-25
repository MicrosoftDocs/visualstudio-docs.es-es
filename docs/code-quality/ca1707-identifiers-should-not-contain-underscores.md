---
title: 'CA1707: Los identificadores no deben contener caracteres de subrayado'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotContainUnderscores
- CA1707
helpviewer_keywords:
- CA1707
- IdentifiersShouldNotContainUnderscores
ms.assetid: 5fb539ef-c304-4323-90c0-b14386da9774
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: adfa0ccd63d0433d367b0e7278693608bb83d685
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234271"
---
# <a name="ca1707-identifiers-should-not-contain-underscores"></a>CA1707: Los identificadores no deben contener caracteres de subrayado

|||
|-|-|
|TypeName|IdentifiersShouldNotContainUnderscores|
|Identificador de comprobación|CA1707|
|Categoría|Microsoft.Naming|
|Cambio importante|Problemático: cuando se produce en ensamblados<br /><br /> No problemático: cuando se produce en parámetros de tipo|

## <a name="cause"></a>Motivo

El nombre de un identificador contiene el carácter de subrayado (\_).

## <a name="rule-description"></a>Descripción de la regla

Por Convención, los nombres de identificador no contienen el carácter de subrayado (\_). La regla comprueba los espacios de nombres, los tipos, los miembros y los parámetros.

Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime. Esto reduce la curva de aprendizaje necesaria para las nuevas bibliotecas de software y aumenta la confianza del cliente respecto a que la biblioteca se haya desarrollado por parte de un especialista en desarrollo de código administrado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Quite todos los caracteres de subrayado del nombre.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

No suprima las advertencias de esta regla.

## <a name="related-rules"></a>Reglas relacionadas

- [CA1709: Los identificadores deben usar mayúsculas y minúsculas correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Los identificadores deben diferir más que el uso de mayúsculas y minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
