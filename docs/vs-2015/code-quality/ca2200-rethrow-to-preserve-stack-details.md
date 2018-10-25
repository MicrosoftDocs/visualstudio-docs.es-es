---
title: 'CA2200: Rethrow para conservar los detalles de la pila | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- RethrowToPreserveStackDetails
- CA2200
helpviewer_keywords:
- CA2200
- RethrowToPreserveStackDetails
ms.assetid: 046e1b98-c4dc-4515-874f-9c0de2285621
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: eb0550a6850f79c7098817d19222c8034e1127ed
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49874805"
---
# <a name="ca2200-rethrow-to-preserve-stack-details"></a>CA2200: Iniciar de nuevo para preservar los detalles de la pila
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|RethrowToPreserveStackDetails|
|Identificador de comprobación|CA2200|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Se vuelve a producir una excepción y la excepción se especifica explícitamente en el `throw` instrucción.

## <a name="rule-description"></a>Descripción de la regla
 Una vez que se produce una excepción, parte de la información que lleva es el seguimiento de pila. El seguimiento de pila es una lista de la jerarquía de llamadas de método que empieza por el método que produce la excepción y termina con el método que detecta la excepción. Si se produce una excepción de nuevo mediante la especificación de la excepción en el `throw` instrucción, se reinicia el seguimiento de pila en el método actual y la lista de llamadas de método entre el método original que produjo la excepción y el método actual se pierde. Para mantener la información de seguimiento de pila original con la excepción, utilice el `throw` instrucción sin especificar la excepción.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, volver a producir la excepción sin especificar explícitamente la excepción.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un método, `CatchAndRethrowExplicitly`, lo que infringe la regla y un método, `CatchAndRethrowImplicitly`, que cumple la regla.

 [!code-csharp[FxCop.Usage.Rethrow#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.Rethrow/cs/FxCop.Usage.Rethrow.cs#1)]
 [!code-vb[FxCop.Usage.Rethrow#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.Rethrow/vb/FxCop.Usage.Rethrow.vb#1)]



