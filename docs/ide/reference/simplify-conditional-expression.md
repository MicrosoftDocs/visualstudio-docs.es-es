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
ms.openlocfilehash: 0242c8c89848e3e76673ddfbca8a27c20605048d
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810355"
---
# <a name="simplify-conditional-expression-refactoring"></a>Simplificación de la refactorización de expresiones condicionales

Esta refactorización se aplica a lo siguiente:

- C#

**Qué:** permite simplificar una [expresión condicional](/dotnet/csharp/language-reference/operators/conditional-operator).

**Cuándo:** quiere quitar el código innecesario para proporcionar mayor claridad.

**Por qué:** simplificar una expresión condicional puede proporcionar una sintaxis más clara y concisa. Esta herramienta de refactorización realizará la tarea automáticamente en lugar de tener que hacerlo manualmente.

## <a name="how-to"></a>Procedimiento

1. Coloque el símbolo de intercalación en la expresión condicional:

2. Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.

3. Seleccione **Simplificar la expresión condicional**.

    ![Simplificación de una expresión condicional](media/simplify-conditional-expression.png)

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)