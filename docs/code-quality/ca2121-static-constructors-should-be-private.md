---
title: 'CA2121: Los constructores estáticos deberían ser privados'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
ms.openlocfilehash: a4955feca4bcdde422001eb22a3117fc7fb524ea
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="ca2121-static-constructors-should-be-private"></a>CA2121: Los constructores estáticos deberían ser privados
|||
|-|-|
|TypeName|StaticConstructorsShouldBePrivate|
|Identificador de comprobación|CA2121|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo tiene un constructor estático que no es privado.

## <a name="rule-description"></a>Descripción de la regla
 Un constructor estático, también conocido como un constructor de clase se utiliza para inicializar un tipo. El sistema llama al constructor estático antes de crear la primera instancia del tipo o antes de hacer referencia a cualquier miembro estático. El usuario no tiene ningún control sobre cuándo se llama al constructor estático. Si un constructor estático no es privado, se puede llamar a través de un código distinto del sistema. En función de las operaciones que se realizan en el constructor, esto puede producir un comportamiento inesperado.

 Esta regla se aplica a los compiladores de C# y Visual Basic.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Infracciones se deben generalmente a una de las siguientes acciones:

-   Define un constructor estático para su tipo y no estableció como privado.

-   El compilador de lenguaje de programación agregó un constructor estático predeterminado a su tipo y no estableció como privado.

 Para corregir el primer tipo de infracción, marque el constructor estático como privado. Para corregir el segundo tipo, agregue un constructor estático privado a su tipo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima estas infracciones. Si el diseño de software requiere una llamada explícita a un constructor estático, es probable que el diseño contenga errores graves y debe revisarse.