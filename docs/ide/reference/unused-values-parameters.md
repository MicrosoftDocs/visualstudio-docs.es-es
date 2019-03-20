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
ms.openlocfilehash: afcf85fff188853890b86cf7deb13b2457f5e0b8
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157703"
---
# <a name="unused-expression-values-and-parameters"></a>Parámetros y valores de expresión no usados

Esta refactorización se aplica a lo siguiente:

- C#
- Visual Basic

**Qué:** Atenúa parámetros no usados y genera una advertencia para valores de expresión no usados.

**Cuándo:** Tiene parámetros o valores de expresión que no se usan nunca.

**Por qué:** A veces es difícil saber si ya no se usa un parámetro o valor. Al atenuar estos valores o generar una advertencia, se obtiene una indicación visual de qué código se puede eliminar.

## <a name="unused-expression-values-and-parameters-diagnostic"></a>Diagnóstico de parámetros y valores de expresión no usados

1. Tiene cualquier valor de expresión o parámetro que no se usa.
2. El parámetro no usado aparece atenuado. El valor de expresión no usado recibe una advertencia.

  ![Parámetro no usado](media/unused-parameter.png)
  ![Valor no usado](media/unused-value.png)

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
- [Sugerencias para desarrolladores de .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)
