---
title: Conversión de una instrucción if a una instrucción o expresión switch
description: Obtenga información sobre cómo usar el menú Acciones rápidas y refactorizaciones para convertir una instrucción if en una instrucción switch o en una expresión switch de C# 8.0.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 0d857338eb1c9b5bb66ccb89e20e6f892944d608
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936835"
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
