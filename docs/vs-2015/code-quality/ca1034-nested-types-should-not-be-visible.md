---
title: 'CA1034: los tipos anidados no deben ser visibles | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
helpviewer_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
ms.assetid: e9789a2c-2540-42a1-8705-ae7104011194
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 04a982c993ffbb04a3e7600dfb93a00e80727b84
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85542173"
---
# <a name="ca1034-nested-types-should-not-be-visible"></a>CA1034: Los tipos anidados no deben ser visibles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|NestedTypesShouldNotBeVisible|
|Identificador de comprobación|CA1034|
|Category|Microsoft. Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 Un tipo visible externamente contiene una declaración de tipos visible externamente. Las enumeraciones anidadas y los tipos protegidos están exentos de esta regla.

## <a name="rule-description"></a>Descripción de la regla
 Un tipo anidado es un tipo declarado dentro del ámbito de otro tipo. Los tipos anidados son útiles para encapsular los detalles de la implementación privada del tipo contenedor. Los tipos anidados, utilizados para este propósito, no deben ser visibles externamente.

 No utilice tipos anidados visibles externamente para la Agrupación lógica o para evitar colisiones de nombres; en su lugar, use los espacios de nombres.

 Los tipos anidados incluyen la noción de accesibilidad de miembros, que algunos programadores no entienden claramente.

 Los tipos protegidos se pueden utilizar en subclases y tipos anidados en escenarios de personalización anticipada.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Si no desea que el tipo anidado esté visible externamente, cambie la accesibilidad del tipo. De lo contrario, quite el tipo anidado de su elemento primario. Si el propósito de la anidación es categorizar el tipo anidado, use un espacio de nombres para crear la jerarquía en su lugar.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un tipo que infringe la regla.

 [!code-cpp[FxCop.Design.NestedTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.NestedTypes/cpp/FxCop.Design.NestedTypes.cpp#1)]
 [!code-csharp[FxCop.Design.NestedTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NestedTypes/cs/FxCop.Design.NestedTypes.cs#1)]
 [!code-vb[FxCop.Design.NestedTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NestedTypes/vb/FxCop.Design.NestedTypes.vb#1)]
