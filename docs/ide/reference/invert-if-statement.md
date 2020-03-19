---
title: Invertir instrucción if
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: a0419100cbc5fcd543eb250fa85cbfe2ebd1c97f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "65531589"
---
# <a name="invert-if-statement"></a>Invertir instrucción if

Esta refactorización se aplica a lo siguiente:

- C#
- Visual Basic

**Qué:** Permite invertir una instrucción `if` o `if else` sin cambiar el significado del código.

**Cuándo:** Cuando tiene una instrucción `if` o `if else` que se entendería mejor al invertirse.

**Por qué:** La inversión manual de una instrucción `if` o `if else` puede llevar bastante más tiempo y, posiblemente, dar lugar a errores. Esta corrección de código ayuda a realizar esta refactorización automáticamente.

## <a name="invert-if-statement-refactoring"></a>Invertir refactorización de instrucción if

1. Coloque el cursor en una instrucción `if` o `if else`.

    ![Invertir if else](media/invert-if.png)

2. Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.

    ![Invert if else code fix](media/invert-if-codefix.png)

3. Seleccione **Invert if** (Invertir if).

    ![Invertir resultado if else](media/invert-if-codefix-result.png)

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
- [Sugerencias para desarrolladores de .NET](../csharp-developer-productivity.md)
