---
title: 'CA1012: Los tipos abstractos no deberían tener constructores'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AbstractTypesShouldNotHaveConstructors
- CA1012
helpviewer_keywords:
- CA1012
ms.assetid: 09f458ac-dd88-4cd7-a47f-4106c1e80ece
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bf4f29a11a831bd5b7d4860dd15698922df3a2c6
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="ca1012-abstract-types-should-not-have-constructors"></a>CA1012: Los tipos abstractos no deberían tener constructores
|||
|-|-|
|TypeName|AbstractTypesShouldNotHaveConstructors|
|Identificador de comprobación|CA1012|
|Categoría|Microsoft.Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un tipo público es abstracto y tiene un constructor público.

## <a name="rule-description"></a>Descripción de la regla
 Los tipos derivados pueden llamar solo a los constructores de tipos abstractos. Puesto que los constructores públicos crean instancias de un tipo y no se pueden crear instancias de un tipo abstracto, no es correcto diseñar un tipo abstracto con un constructor público.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, marque el constructor protegido o no declare el tipo como abstracto.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla. El tipo abstracto tiene un constructor público.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente contiene un tipo abstracto que infringe esta regla.

 [!code-vb[FxCop.Design.AbstractTypeBad#1](../code-quality/codesnippet/VisualBasic/ca1012-abstract-types-should-not-have-constructors_1.vb)]
 [!code-csharp[FxCop.Design.AbstractTypeBad#1](../code-quality/codesnippet/CSharp/ca1012-abstract-types-should-not-have-constructors_1.cs)]

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se corrige la infracción anterior cambiando la accesibilidad del constructor de `public` a `protected`.

 [!code-csharp[FxCop.Design.AbstractTypeGood#1](../code-quality/codesnippet/CSharp/ca1012-abstract-types-should-not-have-constructors_2.cs)]
 [!code-vb[FxCop.Design.AbstractTypeGood#1](../code-quality/codesnippet/VisualBasic/ca1012-abstract-types-should-not-have-constructors_2.vb)]