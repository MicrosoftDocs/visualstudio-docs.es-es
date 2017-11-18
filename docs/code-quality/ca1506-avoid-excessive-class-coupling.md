---
title: 'CA1506: Evite el acoplamiento excesivo de clases | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidExcessiveClassCoupling
- CA1506
helpviewer_keywords:
- AvoidExcessiveClassCoupling
- CA1506
ms.assetid: 9f0943c0-e802-4e3f-8798-2ab8653ddc80
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8192868aa7c5d79039a5e94a2aa13c47ada5d47c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="ca1506-avoid-excessive-class-coupling"></a>CA1506: Evite el acoplamiento excesivo de clases
|||  
|-|-|  
|TypeName|AvoidExcessiveClassCoupling|  
|Identificador de comprobación|CA1506|  
|Categoría|Microsoft.Maintainability|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 Un tipo o método se acopla con muchos otros tipos.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Esta regla mide el acoplamiento de clase contando el número de referencias de tipo únicas que contiene un tipo o método.  
  
 Tipos y métodos que tienen un alto grado de acoplamiento de clase pueden ser difíciles de mantener. Es una buena práctica para tener tipos y métodos que exhiban acoplamiento bajo y alto cohesión.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir esta infracción, intente volver a diseñar el tipo o método para reducir el número de tipos a la que esté acoplado.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Excluir esta advertencia cuando el tipo o método todavía se considera fácil de mantener a pesar de su gran número de dependencias en otros tipos.  
  
## <a name="see-also"></a>Vea también  
 [Advertencias de mantenimiento](../code-quality/maintainability-warnings.md)   
 [Medir la complejidad y el mantenimiento del código administrado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)