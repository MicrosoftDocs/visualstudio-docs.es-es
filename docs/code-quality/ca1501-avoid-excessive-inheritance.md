---
title: 'CA1501: Evite una herencia excesiva | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1501
- AvoidExcessiveInheritance
helpviewer_keywords:
- AvoidExcessiveInheritance
- CA1501
ms.assetid: 9e934746-1a4d-492a-91e4-085201abafa4
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 05d54c668ee6e21932d766272044bd3a7e0aa0e4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="ca1501-avoid-excessive-inheritance"></a>CA1501: Evite una herencia excesiva
|||  
|-|-|  
|TypeName|AvoidExcessiveInheritance|  
|Identificador de comprobación|CA1501|  
|Categoría|Microsoft.Maintainability|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 Un tipo tiene más de cuatro niveles de profundidad en su jerarquía de herencia.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Las jerarquías de tipos con demasiados niveles de anidación pueden resultar difíciles de seguir, comprender y mantener. Esta regla limita el análisis a las jerarquías en el mismo módulo.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, derive el tipo de un tipo base que sea menor profundidad de la jerarquía de herencia o eliminar algunos de los tipos base intermedios.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla. Sin embargo, el código puede ser más difícil de mantener. Tenga en cuenta que, dependiendo de la visibilidad de tipos base, resolver las infracciones de esta regla puede crear cambios importantes. Por ejemplo, quitar los tipos base públicos es un cambio importante.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra un tipo que infringe la regla.  
  
 [!code-csharp[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/CSharp/ca1501-avoid-excessive-inheritance_1.cs)]
 [!code-vb[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/VisualBasic/ca1501-avoid-excessive-inheritance_1.vb)]