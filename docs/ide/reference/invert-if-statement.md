---
title: Invertir instrucción if
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kendrahavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: a6dd0a3ebdb41243734850cea4f4b43604ebb94b
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57324670"
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

2. Presione **Ctrl**+**.** para activar el menú **Acciones rápidas y refactorizaciones**.

    ![Invertir corrección de código if else](media/invert-if-codefix.png)

3. Seleccione **Invert if** (Invertir if).

    ![Invertir resultado if else](media/invert-if-codefix-result.png)

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
- [Sugerencias para desarrolladores de .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)
