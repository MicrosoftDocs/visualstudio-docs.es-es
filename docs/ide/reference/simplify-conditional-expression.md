---
title: Simplificación de una expresión condicional
ms.date: 06/08/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: d0571c01217441d4a39fbfe6fb58ccfe95fd0c5a
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/23/2020
ms.locfileid: "85291045"
---
# <a name="simplify-conditional-expression-refactoring"></a>Simplificación de la refactorización de expresiones condicionales

Esta refactorización se aplica a lo siguiente:

- C#

**Qué:** permite simplificar una [expresión condicional](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator).

**Cuándo:** quiere quitar el código innecesario para proporcionar mayor claridad.

**Por qué:** simplificar una expresión condicional puede proporcionar una sintaxis más clara y concisa. Esta herramienta de refactorización realizará la tarea automáticamente en lugar de tener que hacerlo manualmente.

## <a name="how-to"></a>Procedimiento

1. Coloque el símbolo de intercalación en la expresión condicional:

2. Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.

3. Seleccione **Simplificar la expresión condicional**.

    ![Simplificación de una expresión condicional](media/simplify-conditional-expression.png)

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)