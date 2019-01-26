---
title: 'CA2200: Reiniciar para mantener los detalles de la pila'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- RethrowToPreserveStackDetails
- CA2200
helpviewer_keywords:
- CA2200
- RethrowToPreserveStackDetails
ms.assetid: 046e1b98-c4dc-4515-874f-9c0de2285621
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 6f2dcc8a39e5ad29c590c5f0a7283154bfe1361a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55036399"
---
# <a name="ca2200-rethrow-to-preserve-stack-details"></a>CA2200: Reiniciar para mantener los detalles de la pila

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

Para corregir una infracción de esta regla, vuelva a producir la excepción sin especificar explícitamente la excepción.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra un método, `CatchAndRethrowExplicitly`, lo que infringe la regla y un método, `CatchAndRethrowImplicitly`, que cumple la regla.

[!code-csharp[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/CSharp/ca2200-rethrow-to-preserve-stack-details_1.cs)]
[!code-vb[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/VisualBasic/ca2200-rethrow-to-preserve-stack-details_1.vb)]