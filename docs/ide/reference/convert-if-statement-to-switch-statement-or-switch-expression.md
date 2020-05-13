---
title: Conversión de una instrucción if a una instrucción o expresión switch
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 93ad96809c77d5644b13e6221a41f0b182fb448f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094161"
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
