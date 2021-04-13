---
title: Uso de new()
description: Aprenda a usar `new()` cuando no se puede usar `var`.
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 889be18ab342f515bf5add266088a7ee69c087c1
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2021
ms.locfileid: "106218079"
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
