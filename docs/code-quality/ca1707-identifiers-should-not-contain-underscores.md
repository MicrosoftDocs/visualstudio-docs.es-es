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
ms.openlocfilehash: 5ba9e8dda927edca08565b088cbde90d63443908
ms.sourcegitcommit: 3e94d9fb6dc56fa8b23fbacd5d11cf8d6e7e18f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/10/2019
ms.locfileid: "72252573"
---
# <a name="ca1707-identifiers-should-not-contain-underscores"></a>CA1707: Los identificadores no deben contener caracteres de subrayado

|||
|-|-|
|TypeName|IdentifiersShouldNotContainUnderscores|
|Identificador de comprobación|CA1707|
|Category|Microsoft.Naming|
|Cambio importante|Problemático: cuando se produce en ensamblados<br /><br /> No problemático: cuando se produce en parámetros de tipo|

## <a name="cause"></a>Motivo

El nombre de un identificador contiene el carácter de subrayado (\_).

## <a name="rule-description"></a>Descripción de la regla

Por Convención, los nombres de identificador no contienen el carácter de subrayado (\_). La regla comprueba los espacios de nombres, los tipos, los miembros y los parámetros.

Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime. Esto reduce la curva de aprendizaje necesaria para las nuevas bibliotecas de software y aumenta la confianza del cliente respecto a que la biblioteca se haya desarrollado por parte de un especialista en desarrollo de código administrado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Quite todos los caracteres de subrayado del nombre.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

No suprima las advertencias del código de producción. Sin embargo, es seguro suprimir esta advertencia para el código de prueba. Puede suprimir las advertencias de esta regla estableciendo su [gravedad](use-roslyn-analyzers.md#rule-severity) en **ninguno**. 

## <a name="related-rules"></a>Reglas relacionadas

- [CA1709: Los identificadores deben tener mayúsculas y minúsculas correctamente @ no__t-0
- [CA1708: Los identificadores deben ser diferentes en lugar de Case @ no__t-0
