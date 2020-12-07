---
title: Conversión de una instrucción if a una instrucción o expresión switch
description: Obtenga información sobre cómo usar el menú Acciones rápidas y refactorizaciones para convertir una instrucción if en una instrucción switch o en una expresión switch de C# 8.0.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: e19314b8bf73f5859fdf2cef7d281f142c643b68
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305563"
---
# <a name="convert-if-statement-to-switch-statement-or-switch-expression"></a>Conversión de una instrucción if a una instrucción o expresión switch

Esta refactorización se aplica a lo siguiente:

- C#

**Qué:** Convertir una instrucción if en una [instrucción switch](/dotnet/csharp/language-reference/keywords/switch) o una [expresión switch](/dotnet/csharp/whats-new/csharp-8#switch-expressions) de C# 8.0.

**Cuándo:** Quiere convertir una instrucción `if` en una instrucción `switch` o una expresión `switch`, y viceversa.

**Por qué:** Si solo usa una expresión `if`, esta refactorización permite una transición sencilla a las instrucciones `switch` o las expresiones `switch`.

## <a name="how-to"></a>Procedimiento

1. Coloque el cursor en la palabra clave `if`.
2. Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.
3. Seleccione una de las dos opciones siguientes:

    Seleccione **Convertir en una instrucción 'switch'** .

   ![Conversión de una instrucción "if" en una instrucción "switch"](media/convert-if-to-switch-statement.png)

    Seleccione **Convertir en una expresión "switch"** .

    ![Conversión de una instrucción "if" en una expresión "switch"](media/convert-if-to-switch-expression.png)

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
