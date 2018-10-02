---
title: 'CA1501: Evite una herencia excesiva | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1501
- AvoidExcessiveInheritance
helpviewer_keywords:
- AvoidExcessiveInheritance
- CA1501
ms.assetid: 9e934746-1a4d-492a-91e4-085201abafa4
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: febffd0b9e2fb0275cab1a8055515c83fade5a12
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591613"
---
# <a name="ca1501-avoid-excessive-inheritance"></a>CA1501: Evite una herencia excesiva
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [CA1501: Evite una herencia excesiva](https://docs.microsoft.com/visualstudio/code-quality/ca1501-avoid-excessive-inheritance).

|||
|-|-|
|TypeName|AvoidExcessiveInheritance|
|Identificador de comprobación|CA1501|
|Categoría|Microsoft.Maintainability|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo tiene más de cuatro niveles de profundidad en su jerarquía de herencia.

## <a name="rule-description"></a>Descripción de la regla
 Las jerarquías de tipos con demasiados niveles de anidación pueden resultar difíciles de seguir, comprender y mantener. Esta regla limita analysis a jerarquías en el mismo módulo.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, derive el tipo de un tipo base que es menos profundo en la jerarquía de herencia o eliminar algunos de los tipos base intermedios.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla. Sin embargo, el código sea más difícil de mantener. Tenga en cuenta que, dependiendo de la visibilidad de tipos base, resolver las infracciones de esta regla podría crear cambios importantes. Por ejemplo, la eliminación de tipos bases públicos es un cambio importante.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un tipo que infringe la regla.

 [!code-csharp[FxCop.Maintainability.ExcessiveInheritance#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.ExcessiveInheritance/cs/FxCop.Maintainability.ExcessiveInheritance.cs#1)]
 [!code-vb[FxCop.Maintainability.ExcessiveInheritance#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.ExcessiveInheritance/vb/FxCop.Maintainability.ExcessiveInheritance.vb#1)]



