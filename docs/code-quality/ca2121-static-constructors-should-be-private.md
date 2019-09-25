---
title: 'CA2121: Los constructores estáticos deben ser privados'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2121
- StaticConstructorsShouldBePrivate
helpviewer_keywords:
- CA2121
- StaticConstructorsShouldBePrivate
ms.assetid: ee93c620-8fc1-4e47-866c-d389c3ca9f2e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b52f4412b1b048c41033f74200828f70361c1ea3
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232505"
---
# <a name="ca2121-static-constructors-should-be-private"></a>CA2121: Los constructores estáticos deben ser privados

|||
|-|-|
|TypeName|StaticConstructorsShouldBePrivate|
|Identificador de comprobación|CA2121|
|Categoría|Microsoft.Security|
|Cambio importante|Problemático|

## <a name="cause"></a>Motivo

Un tipo tiene un constructor estático que no es privado.

## <a name="rule-description"></a>Descripción de la regla

Un constructor estático, también conocido como constructor de clase, se usa para inicializar un tipo. El sistema llama al constructor estático antes de crear la primera instancia del tipo o antes de hacer referencia a cualquier miembro estático. El usuario no tiene control sobre cuándo se llama al constructor estático. Si un constructor estático no es privado, se puede llamar a través de un código distinto del sistema. En función de las operaciones que se realizan en el constructor, esto puede producir un comportamiento inesperado.

Esta regla la aplican los C# compiladores y Visual Basic.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Las infracciones suelen deberse a una de las siguientes acciones:

- Definió un constructor estático para el tipo y no lo hizo privado.

- El compilador del lenguaje de programación agregó un constructor estático predeterminado al tipo y no lo hizo privado.

Para corregir el primer tipo de infracción, haga que el constructor estático sea privado. Para corregir el segundo tipo, agregue un constructor estático privado al tipo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

No suprima estas infracciones. Si el diseño de software requiere una llamada explícita a un constructor estático, es probable que el diseño contenga errores graves y se revise.