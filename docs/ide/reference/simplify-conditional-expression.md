---
title: Simplificación de una expresión condicional
description: Obtenga información sobre cómo usar el menú Acciones rápidas y refactorizaciones para simplificar una expresión condicional.
ms.custom: SEO-VS-2020
ms.date: 06/08/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: dd7b3f29e804ec5e925c34f7994164d5a8465a50
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480218"
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