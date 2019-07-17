---
title: 'CA1012: Tipos abstractos no deberían tener constructores | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AbstractTypesShouldNotHaveConstructors
- CA1012
helpviewer_keywords:
- CA1012
ms.assetid: 09f458ac-dd88-4cd7-a47f-4106c1e80ece
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 02b92ac92e545ab30405d195d85a97a4ef2e3806
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68151088"
---
# <a name="ca1012-abstract-types-should-not-have-constructors"></a>CA1012: Los tipos abstractos no deberían tener constructores
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AbstractTypesShouldNotHaveConstructors|
|Identificador de comprobación|CA1012|
|Categoría|Microsoft.Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
 Un tipo público es abstracto y tiene un constructor público.

## <a name="rule-description"></a>Descripción de la regla
 Los tipos derivados pueden llamar solo a los constructores de tipos abstractos. Puesto que los constructores públicos crean instancias de un tipo y no se pueden crear instancias de un tipo abstracto, no es correcto diseñar un tipo abstracto con un constructor público.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, marque el constructor protegido o no declare el tipo como abstracto.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla. El tipo abstracto tiene un constructor público.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente contiene un tipo abstracto que infringe esta regla.

 [!code-csharp[FxCop.Design.AbstractTypeBad#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AbstractTypeBad/cs/FxCop.Design.AbstractTypeBad.cs#1)]
 [!code-vb[FxCop.Design.AbstractTypeBad#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AbstractTypeBad/vb/FxCop.Design.AbstractTypeBad.vb#1)]

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se corrige la infracción anterior cambiando la accesibilidad del constructor de `public` a `protected`.

 [!code-csharp[FxCop.Design.AbstractTypeGood#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AbstractTypeGood/cs/FxCop.Design.AbstractTypeGood.cs#1)]
 [!code-vb[FxCop.Design.AbstractTypeGood#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AbstractTypeGood/vb/FxCop.Design.AbstractTypeGood.vb#1)]
