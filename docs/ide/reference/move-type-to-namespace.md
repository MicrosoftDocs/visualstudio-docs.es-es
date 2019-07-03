---
title: Traslado de tipo al espacio de nombres
ms.date: 06/17/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 821e915a0b66f25c5b89a83b31e93b01aea6f400
ms.sourcegitcommit: b593bb889f049fcbdff502c30b73178ed17dbdf0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/20/2019
ms.locfileid: "67292706"
---
# <a name="move-type-to-namespace"></a>Traslado de tipo al espacio de nombres

Esta refactorización se aplica a lo siguiente:

- C#

**Qué:** Traslado de tipo al espacio de nombres.

**Cuándo:** Desea trasladar un tipo a un espacio de nombres diferente o una carpeta. 

**Por qué:** Quiere refactorizar las partes de la solución y tiene una forma rápida de trasladar un tipo a un espacio de nombres diferente o una carpeta. 

## <a name="how-to"></a>Procedimiento

1. Coloque el cursor en el nombre de clase.
2. Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.
3. Seleccione **Move to namespace** (Trasladar al espacio de nombres).

   ![Traslado a la refactorización del espacio de nombres](media/move-to-namespace.png)

4. En el cuadro de diálogo que aparece, seleccione el espacio de nombres de destino al que desea trasladar el tipo. 

   ![Selección de un cuadro de diálogo de espacio de nombres](media/select-target-namespace.png)

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
