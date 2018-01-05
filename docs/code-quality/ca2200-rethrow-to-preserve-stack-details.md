---
title: 'CA2200: Rethrow para conservar los detalles de la pila | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- RethrowToPreserveStackDetails
- CA2200
helpviewer_keywords:
- CA2200
- RethrowToPreserveStackDetails
ms.assetid: 046e1b98-c4dc-4515-874f-9c0de2285621
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 81dff0b9e876719fdfd26409772498390344cd2c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
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