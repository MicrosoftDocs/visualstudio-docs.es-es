---
title: Extraer función local
description: Convierta un fragmento de código en su propio método; para ello, seleccione el código y escriba Ctrl+R, Ctrl+M.
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 031fbe22ec61837d489df7a6af923ef0cd2454c7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "77519330"
---
# <a name="extract-local-function-refactoring"></a>Refactorización Extraer función local

Esta refactorización se aplica a lo siguiente:

- C#

**Qué:** permite convertir un fragmento de código de un método existente en una función local.

**Cuándo:** tiene un fragmento de código existente en algún método al que se debe llamar desde una función local.

**Por qué:** Se podría copiar y pegar ese código, pero eso provocaría una duplicación. Una mejor solución es refactorizar ese fragmento en su propia función local.

## <a name="how-to"></a>Procedimiento

1. Resalte el código que se va a extraer.

2. Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**. 

3. Seleccione **Extraer función local**.

    ![Extraer función local](media/extract-local-function.png)

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
- [Vista previa de cambios](../../ide/preview-changes.md)
