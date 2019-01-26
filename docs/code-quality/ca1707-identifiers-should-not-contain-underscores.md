---
title: 'CA1707: Los identificadores no deben contener caracteres de subrayado'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: bb7fc19f90b7f0cd329dd1cff972d08c2052b055
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54951383"
---
# <a name="ca1707-identifiers-should-not-contain-underscores"></a>CA1707: Los identificadores no deben contener caracteres de subrayado

|||
|-|-|
|TypeName|IdentifiersShouldNotContainUnderscores|
|Identificador de comprobación|CA1707|
|Categoría|Microsoft.Naming|
|Cambio problemático|Problemático: cuando se desencadena en ensamblados<br /><br /> No problemático: cuando se produce en parámetros de tipo|

## <a name="cause"></a>Motivo

El nombre de un identificador contiene el carácter de subrayado (\_) caracteres.

## <a name="rule-description"></a>Descripción de la regla

Por convención, los nombres de identificador no contienen el carácter de subrayado (\_) caracteres. La regla comprueba espacios de nombres, tipos, miembros y parámetros.

Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime. Esto reduce la curva de aprendizaje necesaria para las nuevas bibliotecas de software y aumenta la confianza del cliente respecto a que la biblioteca se haya desarrollado por parte de un especialista en desarrollo de código administrado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Quite todos los caracteres de subrayado del nombre.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

No suprima las advertencias de esta regla.

## <a name="related-rules"></a>Reglas relacionadas

- [CA1709: Los identificadores deberían escribirse correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Los identificadores deben diferenciarse por algo más que el caso](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
