---
title: Uso de new()
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: a129e94f6009eec51995b6a4e170f0a804e6407f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889816"
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
