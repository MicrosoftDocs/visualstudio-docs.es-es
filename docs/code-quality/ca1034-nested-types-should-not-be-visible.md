---
title: 'CA1034: Los tipos anidados no deben ser visibles | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
helpviewer_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
ms.assetid: e9789a2c-2540-42a1-8705-ae7104011194
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bb549e50f33ac172f1eaa0e2a4489cd1900d0542
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="ca1034-nested-types-should-not-be-visible"></a>CA1034: Los tipos anidados no deben ser visibles
|||  
|-|-|  
|TypeName|NestedTypesShouldNotBeVisible|  
|Identificador de comprobación|CA1034|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 Un tipo visible externamente contiene una declaración de tipo visible externamente. Las enumeraciones anidadas y los tipos protegidos están exentos de esta regla.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Un tipo anidado es un tipo declarado dentro del ámbito de otro tipo. Los tipos anidados son útiles para encapsular los detalles de la implementación privada del tipo contenedor. Los tipos anidados, utilizados para este propósito, no deben ser visibles externamente.  
  
 No utilice tipos anidados visibles externamente para agrupación lógica o para evitar conflictos de nombres; en su lugar, utilice los espacios de nombres.  
  
 Los tipos anidados incluyen la noción de accesibilidad de miembro, que algunos programadores no entienden claramente.  
  
 Tipos protegidos se pueden usar en las subclases y los tipos anidados en escenarios de personalización avanzada.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Si no desea que el tipo anidado esté visible externamente, cambie la accesibilidad del tipo. De lo contrario, quite el tipo anidado de su elemento primario. Si el propósito del anidamiento es clasificar el tipo anidado, utilice un espacio de nombres para crear la jerarquía en su lugar.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra un tipo que infringe la regla.  
  
 [!code-cpp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CPP/ca1034-nested-types-should-not-be-visible_1.cpp)]
 [!code-csharp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CSharp/ca1034-nested-types-should-not-be-visible_1.cs)]
 [!code-vb[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/VisualBasic/ca1034-nested-types-should-not-be-visible_1.vb)]