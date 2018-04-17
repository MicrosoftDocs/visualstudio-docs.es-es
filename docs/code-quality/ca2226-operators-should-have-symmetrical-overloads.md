---
title: 'CA2226: Los operadores deben tener sobrecargar simétricas | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
helpviewer_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
ms.assetid: d202401a-ea14-4559-b15e-0ea4f5b68789
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 17ce9653f5763788b8a6988994c379fc885152ad
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ca2226-operators-should-have-symmetrical-overloads"></a>CA2226: Los operadores deben tener sobrecargar simétricas
|||  
|-|-|  
|TypeName|OperatorsShouldHaveSymmetricalOverloads|  
|Identificador de comprobación|CA2226|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|No trascendental|  
  
## <a name="cause"></a>Motivo  
 Un tipo implementa el operador de igualdad o de desigualdad y no implementa el operador opuesto.  
  
## <a name="rule-description"></a>Descripción de la regla  
 No hay ningún caso donde es aplicable a las instancias de un tipo de igualdad o desigualdad y no está definido el operador opuesto. Tipos normalmente implementan el operador de desigualdad devolviendo el valor negado del operador de igualdad.  
  
 El compilador de C# emite un error para las infracciones de esta regla.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, implemente la igualdad y los operadores de desigualdad o quitar el elemento que está presente.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla. Su tipo no funcionará de manera coherente con el [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [CA1046: No sobrecargar el operador de igualdad en los tipos de referencia](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225: Las sobrecargas del operador tienen alternativas con nombre](../code-quality/ca2225-operator-overloads-have-named-alternates.md)  
  
 [CA2224: Invalidar Equals al sobrecargar operadores de igualdad](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2218: Invalidar el método GetHashCode al invalidar el método Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)  
  
 [CA2231: Sobrecargar el operador equals al invalidar ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)