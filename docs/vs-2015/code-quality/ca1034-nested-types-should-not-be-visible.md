---
title: 'CA1034: Tipos anidados no deben ser visibles | Documentos de Microsoft'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 915b5807f7b14269acf4b7509ffceaecfb13af47
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58996367"
---
# <a name="ca1034-nested-types-should-not-be-visible"></a>CA1034: Los tipos anidados no deben ser visibles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
