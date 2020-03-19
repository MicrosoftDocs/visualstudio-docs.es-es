---
title: Parámetros y valores no usados
ms.date: 02/15/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: ce2b0f1e0c0db45c478c3917306683b314da0564
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "65531877"
---
# <a name="unused-value-assignments-variables-and-parameters"></a>Parámetros, variables y asignaciones de valor sin usar

Esta refactorización se aplica a lo siguiente:

- C#
- Visual Basic

**Qué:** Atenúa parámetros no usados y genera una advertencia para valores de expresión no usados. El compilador también realiza un análisis de flujo para buscar las asignaciones de valor sin usar. Las asignaciones de valor sin usar se atenúan y aparece una bombilla con una [Acción rápida](../quick-actions.md) para quitar la asignación redundante. Las variables sin usar con valores desconocidos muestran una sugerencia de [Acción rápida](../quick-actions.md) para usar [descartes](/dotnet/csharp/discards) en su lugar. (Los descartes son variables temporales y ficticias que no se usan deliberadamente en el código de la aplicación. Pueden reducir la asignación de memoria y hacer que el código sea más fácil de leer).

**Cuándo:** Tiene asignaciones de valor, parámetros o valores de expresión que no se usan nunca.

**Por qué:** A veces es difícil saber si una asignación de valor, una variable o un parámetro ya no se usan. Al atenuar estos valores o generar una advertencia, se obtiene una indicación visual del código que se puede eliminar.

## <a name="unused-expression-values-and-parameters-diagnostic"></a>Diagnóstico de parámetros y valores de expresión no usados

1. Tiene cualquier asignación de valor, variable o parámetro que no se utilizan.
2. La asignación de valor o el parámetro que no se utilizan aparecen atenuados. El valor de expresión que no se utiliza genera una advertencia.

  ![Parámetro sin usar](media/unused-parameter.png)
  ![Valor sin usar](media/unused-value.png)
  ![Asignación de valor sin usar](media/unused-value-assignment.png)
  ![Descarte de valor sin usar](media/unused-value-discard.png)

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
- [Sugerencias para desarrolladores de .NET](../csharp-developer-productivity.md)
