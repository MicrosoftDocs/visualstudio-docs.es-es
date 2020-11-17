---
title: Uso de new()
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: b2091c046efac9f5676e5d2d99ef798283b95f6e
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2020
ms.locfileid: "93403588"
---
# <a name="use-new"></a>Use `new()`

Esto se aplica a lo siguiente:

- C#

**Qué:** Use `new()`.

**Cuándo:** Tiene un campo que no puede usar `var` o una preferencia de código de estilo para no usar `var`.

**Por qué:** Para que no tenga que escribir código repetitivo dos veces.

## <a name="how-to"></a>Procedimiento

1. Coloque el cursor de inserción en la declaración de campo.

2. Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.

3. Seleccione **Use 'new(…)'** (Usar 'new(…)'):

    ![Use 'new(…)'](media/use-new.png)

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
