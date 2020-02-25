---
title: Conversión de una instrucción if a una instrucción o expresión switch
ms.date: 02/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: cb0c06fe0493f973ea9cf0a566ffda45a49eeeff
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2020
ms.locfileid: "77283464"
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
3. Seleccione **Convertir en una instrucción 'switch'** .

   ![Conversión de una instrucción if a una instrucción o expresión switch](media/convert-if-statement-to-switch-statement-or-switch-expression.png) 

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
