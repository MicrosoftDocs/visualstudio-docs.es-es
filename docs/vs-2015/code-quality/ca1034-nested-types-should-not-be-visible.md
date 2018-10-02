---
title: 'CA1034: Los tipos anidados no deben ser visibles | Microsoft Docs'
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
- NestedTypesShouldNotBeVisible
- CA1034
helpviewer_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
ms.assetid: e9789a2c-2540-42a1-8705-ae7104011194
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5edfdca7fe3834160a7120528b56a2770924bf83
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591686"
---
# <a name="ca1034-nested-types-should-not-be-visible"></a>CA1034: Los tipos anidados no deben ser visibles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [CA1034: los tipos anidados no deben ser visibles](https://docs.microsoft.com/visualstudio/code-quality/ca1034-nested-types-should-not-be-visible).

|||
|-|-|
|TypeName|NestedTypesShouldNotBeVisible|
|Identificador de comprobación|CA1034|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo visible externamente contiene una declaración de tipos visibles externamente. Las enumeraciones anidadas y los tipos protegidos están exentos de esta regla.

## <a name="rule-description"></a>Descripción de la regla
 Un tipo anidado es un tipo declarado dentro del ámbito de otro tipo. Los tipos anidados son útiles para encapsular los detalles de la implementación privada del tipo contenedor. Los tipos anidados, utilizados para este propósito, no deben ser visibles externamente.

 No utilice tipos anidados visibles externamente para agrupación lógica o para evitar conflictos de nombres; en su lugar, use los espacios de nombres.

 Los tipos anidados incluyen la noción de accesibilidad de miembro, que algunos programadores no entienden con claridad.

 Los tipos protegidos pueden usarse en subclases y los tipos anidados en escenarios de personalización avanzada.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Si no desea que el tipo anidado que esté visible externamente, cambie la accesibilidad del tipo. En caso contrario, quite el tipo anidado de su elemento primario. Si el propósito del anidamiento es clasificar el tipo anidado, utilice un espacio de nombres para crear la jerarquía en su lugar.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un tipo que infringe la regla.

 [!code-cpp[FxCop.Design.NestedTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.NestedTypes/cpp/FxCop.Design.NestedTypes.cpp#1)]
 [!code-csharp[FxCop.Design.NestedTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NestedTypes/cs/FxCop.Design.NestedTypes.cs#1)]
 [!code-vb[FxCop.Design.NestedTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NestedTypes/vb/FxCop.Design.NestedTypes.vb#1)]



