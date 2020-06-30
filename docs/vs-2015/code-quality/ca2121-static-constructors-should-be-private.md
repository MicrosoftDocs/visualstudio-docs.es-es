---
title: 'CA2121: los constructores estáticos deben ser privados | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2121
- StaticConstructorsShouldBePrivate
helpviewer_keywords:
- CA2121
- StaticConstructorsShouldBePrivate
ms.assetid: ee93c620-8fc1-4e47-866c-d389c3ca9f2e
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7f95b33e1391ca755a6c0df261fa2bd05bd3c7a0
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544318"
---
# <a name="ca2121-static-constructors-should-be-private"></a>CA2121: Los constructores estáticos deben ser privados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|StaticConstructorsShouldBePrivate|
|Identificador de comprobación|CA2121|
|Category|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 Un tipo tiene un constructor estático que no es privado.

## <a name="rule-description"></a>Descripción de la regla
 Un constructor estático, también conocido como constructor de clase, se usa para inicializar un tipo. El sistema llama al constructor estático antes de crear la primera instancia del tipo o antes de hacer referencia a cualquier miembro estático. El usuario no tiene control sobre cuándo se llama al constructor estático. Si un constructor estático no es privado, se puede llamar a través de un código distinto del sistema. En función de las operaciones que se realizan en el constructor, esto puede producir un comportamiento inesperado.

 Esta regla la aplican los compiladores de C# y Visual Basic .NET.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Las infracciones suelen deberse a una de las siguientes acciones:

- Definió un constructor estático para el tipo y no lo hizo privado.

- El compilador del lenguaje de programación agregó un constructor estático predeterminado al tipo y no lo hizo privado.

  Para corregir el primer tipo de infracción, haga que el constructor estático sea privado. Para corregir el segundo tipo, agregue un constructor estático privado al tipo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima estas infracciones. Si el diseño de software requiere una llamada explícita a un constructor estático, es probable que el diseño contenga errores graves y se revise.
