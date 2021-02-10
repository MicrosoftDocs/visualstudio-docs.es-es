---
title: Instrucciones de división o combinación "if".
description: Obtenga información sobre cómo usar el menú Acciones rápidas y refactorizaciones para dividir o combinar instrucciones if.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 30ec77382cf404bc74f2ff5fed71cff360b9f28e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893391"
---
# <a name="split-or-merge-if-statements"></a>Instrucciones de división o combinación "if".

Esta refactorización se aplica a lo siguiente:

- C#

- Visual Basic

**Qué:** **Qué:** instrucciones de división o combinación [if](/dotnet/csharp/language-reference/keywords/if-else).

**Cuándo:** desea dividir una instrucción `if` que usa los operadores `&&` o `||` en una instrucción `if` anidada, o bien combinar una instrucción `if` con una instrucción `if` externa.

**Por qué:** es una cuestión de preferencia de estilo.  

## <a name="how-to"></a>Instrucciones

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