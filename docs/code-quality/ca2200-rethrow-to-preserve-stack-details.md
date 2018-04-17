---
title: 'CA2200: Rethrow para conservar los detalles de la pila | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- RethrowToPreserveStackDetails
- CA2200
helpviewer_keywords:
- CA2200
- RethrowToPreserveStackDetails
ms.assetid: 046e1b98-c4dc-4515-874f-9c0de2285621
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 18fe55136ca501974b33a04513905ff17fe19748
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ca2200-rethrow-to-preserve-stack-details"></a>CA2200: Iniciar de nuevo para preservar los detalles de la pila
|||  
|-|-|  
|TypeName|RethrowToPreserveStackDetails|  
|Identificador de comprobación|CA2200|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|No trascendental|  
  
## <a name="cause"></a>Motivo  
 Se vuelve a producir una excepción y la excepción se especifica explícitamente en la `throw` instrucción.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Una vez que se produce una excepción, parte de la información que lleva es el seguimiento de pila. El seguimiento de pila es una lista de la jerarquía de llamadas de método que empieza por el método que produce la excepción y termina con el método que detecta la excepción. Si se produce una excepción de nuevo mediante la especificación de la excepción en el `throw` instrucción, el seguimiento de pila se reinicia en el método actual y se pierde la lista de llamadas al método entre el método original que produjo la excepción y el método actual. Para conservar la información de seguimiento de pila original con la excepción, use la `throw` instrucción sin especificar la excepción.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, volver a producir la excepción sin especificar explícitamente la excepción.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra un método, `CatchAndRethrowExplicitly`, lo que infringe la regla y un método, `CatchAndRethrowImplicitly`, que cumple la regla.  
  
 [!code-csharp[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/CSharp/ca2200-rethrow-to-preserve-stack-details_1.cs)]
 [!code-vb[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/VisualBasic/ca2200-rethrow-to-preserve-stack-details_1.vb)]