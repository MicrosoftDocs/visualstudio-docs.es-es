---
title: "CA1026: No se debería utilizar parámetros predeterminados | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
helpviewer_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
ms.assetid: 09643415-36ef-4d0f-9411-5721e14e2512
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0d7a850c959787282cdf6f9d24b392ef4684b7dd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="ca1026-default-parameters-should-not-be-used"></a>CA1026: No debería utilizar parámetros predeterminados
|||  
|-|-|  
|TypeName|DefaultParametersShouldNotBeUsed|  
|Identificador de comprobación|CA1026|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 Un tipo visible externamente contiene un método visible externamente que utiliza un parámetro predeterminado.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Los métodos que utilizan parámetros predeterminados están permitidos en Common Language Specification (CLS); Sin embargo, CLS permite que los compiladores omitan los valores asignados a estos parámetros. Código que se escribe para los compiladores omitan los valores de parámetro predeterminado debe proporcionar explícitamente los argumentos para cada parámetro predeterminado. Para mantener el comportamiento que desea en los lenguajes de programación, los métodos que utilizan parámetros predeterminados deberían reemplazarse con sobrecargas de método que proporcionen los parámetros predeterminados.  
  
 Cuando tiene acceso a código administrado, el compilador omite los valores de parámetros predeterminados de extensión administrada para C++. El compilador de Visual Basic admite métodos con parámetros predeterminados que utilizan la [opcional](/dotnet/visual-basic/language-reference/modifiers/optional) palabra clave.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, reemplace el método que utiliza los parámetros predeterminados con sobrecargas de método que proporcionan los parámetros predeterminados.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra un método que utiliza los parámetros predeterminados y los métodos sobrecargados que proporcionan una funcionalidad equivalente.  
  
 [!code-vb[FxCop.Design.DefaultParameters#1](../code-quality/codesnippet/VisualBasic/ca1026-default-parameters-should-not-be-used_1.vb)]  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [CA1025: Reemplaza argumentos repetitivos con una matriz de parámetros](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)  
  
## <a name="see-also"></a>Vea también  
 [Independencia del lenguaje y componentes independientes del lenguaje](http://msdn.microsoft.com/Library/4f0b77d0-4844-464f-af73-6e06bedeafc6)