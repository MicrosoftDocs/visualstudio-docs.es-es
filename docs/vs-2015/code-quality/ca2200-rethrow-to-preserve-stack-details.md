---
title: 'CA2200: Rethrow para conservar los detalles de la pila | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- RethrowToPreserveStackDetails
- CA2200
helpviewer_keywords:
- CA2200
- RethrowToPreserveStackDetails
ms.assetid: 046e1b98-c4dc-4515-874f-9c0de2285621
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d20407d7cc708ac785e4a792bf8e64768ea58540
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667392"
---
# <a name="ca2200-rethrow-to-preserve-stack-details"></a>CA2200: Iniciar de nuevo para preservar los detalles de la pila
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|RethrowToPreserveStackDetails|
|Identificador de comprobación|CA2200|
|Categoría|Microsoft. Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Se vuelve a producir una excepción y la excepción se especifica explícitamente en la instrucción `throw`.

## <a name="rule-description"></a>Descripción de la regla
 Una vez que se produce una excepción, parte de la información que conlleva es el seguimiento de la pila. El seguimiento de la pila es una lista de la jerarquía de llamadas al método que comienza con el método que produce la excepción y termina con el método que detecta la excepción. Si se vuelve a producir una excepción mediante la especificación de la excepción en la instrucción `throw`, el seguimiento de la pila se reinicia en el método actual y se pierde la lista de llamadas a métodos entre el método original que produjo la excepción y el método actual. Para mantener la información de seguimiento de la pila original con la excepción, use la instrucción `throw` sin especificar la excepción.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, vuelva a iniciar la excepción sin especificar la excepción explícitamente.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un método, `CatchAndRethrowExplicitly`, que infringe la regla y un método, `CatchAndRethrowImplicitly`, que cumple la regla.

 [!code-csharp[FxCop.Usage.Rethrow#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.Rethrow/cs/FxCop.Usage.Rethrow.cs#1)]
 [!code-vb[FxCop.Usage.Rethrow#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.Rethrow/vb/FxCop.Usage.Rethrow.vb#1)]
