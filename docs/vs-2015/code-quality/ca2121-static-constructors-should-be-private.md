---
title: 'CA2121: Los constructores estáticos deberían ser privados | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2121
- StaticConstructorsShouldBePrivate
helpviewer_keywords:
- CA2121
- StaticConstructorsShouldBePrivate
ms.assetid: ee93c620-8fc1-4e47-866c-d389c3ca9f2e
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 9425cabbc024e445df97d9b909f1803b7a972571
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49267324"
---
# <a name="ca2121-static-constructors-should-be-private"></a>CA2121: Los constructores estáticos deberían ser privados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
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

 Esta regla se aplica a los compiladores de C# y Visual Basic. NET.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Infracciones suelen deberse a una de las acciones siguientes:

-   Define un constructor estático para su tipo y no lo estableció como privado.

-   El compilador de lenguaje de programación agregó un constructor estático predeterminado a su tipo y no lo estableció como privado.

 Para corregir el primer tipo de infracción, hacer privado el constructor estático. Para corregir el segundo tipo, agregue un constructor estático privado a su tipo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima estas infracciones. Si el diseño de software requiere una llamada explícita a un constructor estático, es probable que el diseño contenga errores graves y debe revisarse.



