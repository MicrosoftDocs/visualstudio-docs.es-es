---
title: 'CA2121: Los constructores estáticos deben ser privados'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 124d65f1147bbc9aa0d38b2bca8f742bf1b60a9b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53954268"
---
# <a name="ca2121-static-constructors-should-be-private"></a>CA2121: Los constructores estáticos deben ser privados

|||
|-|-|
|TypeName|StaticConstructorsShouldBePrivate|
|Identificador de comprobación|CA2121|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo

Un tipo tiene un constructor estático que no es privado.

## <a name="rule-description"></a>Descripción de la regla

Un constructor estático, también conocido como un constructor de clase se utiliza para inicializar un tipo. El sistema llama al constructor estático antes de crear la primera instancia del tipo o antes de hacer referencia a cualquier miembro estático. El usuario no tiene control sobre cuando se llama al constructor estático. Si un constructor estático no es privado, se puede llamar a través de un código distinto del sistema. En función de las operaciones que se realizan en el constructor, esto puede producir un comportamiento inesperado.

Esta regla se aplica a los compiladores de C# y Visual Basic.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Infracciones suelen deberse a una de las acciones siguientes:

- Define un constructor estático para su tipo y no lo estableció como privado.

- El compilador de lenguaje de programación agregó un constructor estático predeterminado a su tipo y no lo estableció como privado.

Para corregir el primer tipo de infracción, hacer privado el constructor estático. Para corregir el segundo tipo, agregue un constructor estático privado a su tipo.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

No suprima estas infracciones. Si el diseño de software requiere una llamada explícita a un constructor estático, es probable que el diseño contenga errores graves y debe revisarse.