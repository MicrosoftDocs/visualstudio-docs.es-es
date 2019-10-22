---
title: Instrucciones de división o combinación "if".
ms.date: 06/12/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 405ccd4bc0197ce06aa14982a16dc02f6d13a537
ms.sourcegitcommit: d4920babfc3d24a3fe1d4bf446ed3fe73b344467
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/17/2019
ms.locfileid: "67160741"
---
# <a name="split-or-merge-if-statements"></a>Instrucciones de división o combinación "if".

Esta refactorización se aplica a lo siguiente:

- C#

**Qué:** **Qué:** instrucciones de división o combinación [if](/dotnet/csharp/language-reference/keywords/if-else).

**Cuándo:** desea dividir una instrucción `if` que usa los operadores `&&` o `||` en una instrucción `if` anidada, o bien combinar una instrucción `if` con una instrucción `if` externa.

**Por qué:** es una cuestión de preferencia de estilo.  

## <a name="how-to"></a>Procedimiento

Si desea dividir la instrucción `if`:

1. Coloque el cursor en la instrucción `if` por el operador `&&` o `||`.

2. Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.

    ![Dividir instrucción if](../media/split-if-statement.png)

3. Seleccione **Split into nested if statements** (Dividir en instrucciones if anidadas).

    ![Dividir instrucción if completa](../media/split-if-statement-complete.png)

Si desea combinar la instrucción `if` interna con la instrucción `if` externa: 

1. Coloque el cursor en la palabra clave `if` interna.

2. Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.

    ![Combinar instrucción if](../media/merge-if-statement.png)

3. Seleccione **Merge with outer if statement** (Combinar con instrucción if externa).

    ![Combinar instrucción if completa](../media/merge-if-statement-complete.png)

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)