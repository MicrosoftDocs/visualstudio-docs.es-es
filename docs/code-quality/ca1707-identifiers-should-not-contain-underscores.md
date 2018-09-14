---
title: 'CA1707: Los identificadores no deberían contener subrayado'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 74746897f8ce27a79f666ae1d691b235035b4626
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548603"
---
# <a name="ca1707-identifiers-should-not-contain-underscores"></a>CA1707: Los identificadores no deberían contener subrayado

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

- [CA1709: Los identificadores deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Los identificadores se deberían diferenciar en algo más que en el uso de mayúsculas y minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
