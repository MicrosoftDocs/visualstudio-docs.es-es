---
title: 'CA2130: Las constantes críticas de seguridad deberían ser transparentes | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2130
ms.assetid: 344c7f7b-9130-4675-ae7f-9fa260cc9789
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2fbda0886fe05d22ccf61f36792d8bfcf687547a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ca2130-security-critical-constants-should-be-transparent"></a>CA2130: Las constantes críticas para la seguridad deben ser transparentes
|||  
|-|-|  
|TypeName|ConstantsShouldBeTransparent|  
|Identificador de comprobación|CA2130|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 Un campo constante o un miembro de enumeración se marca con la <xref:System.Security.SecurityCriticalAttribute>.  
  
## <a name="rule-description"></a>Descripción de la regla  
 El cumplimiento de la transparencia no se exige para los valores constantes porque los compiladores alinean los valores constantes para que no se requiera ninguna búsqueda en tiempo de ejecución. Los campos constantes deberían ser transparentes en seguridad de modo que los revisores del código no supongan que el código transparente no puede tener acceso a la constante.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, quite el atributo SecurityCritical del campo o valor.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## <a name="example"></a>Ejemplo  
 En los ejemplos siguientes, el valor de enumeración `EnumWithCriticalValues.CriticalEnumValue` y la constante `CriticalConstant` genera esta advertencia. Para corregir los problemas, quite el [`SecurityCritical`] atributo para que sean seguridad transparente.  
  
 [!code-csharp[FxCop.Security.CA2130.ConstantsShouldBeTransparent#1](../code-quality/codesnippet/CSharp/ca2130-security-critical-constants-should-be-transparent_1.cs)]