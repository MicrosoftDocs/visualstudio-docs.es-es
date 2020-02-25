---
title: Introducción a la interpolación de cadenas
ms.date: 02/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 15f034b0ecf46e19681f3b74e4137a2de9e9d950
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2020
ms.locfileid: "77283440"
---
# <a name="simplify-string-interpolation-refactoring"></a>Simplificación de la refactorización de interpolación de cadena

Esta refactorización se aplica a lo siguiente:

- C#

**Qué:** Le permite simplificar una [interpolación de cadena](https://docs.microsoft.com/dotnet/csharp/tutorials/string-interpolation).

**Cuándo:** Tiene una interpolación de cadena que se puede simplificar.

**Por qué:** La simplificación de una interpolación de cadena puede aportar más claridad y una sintaxis más concisa. Esta herramienta de refactorización realizará la tarea automáticamente en lugar de tener que hacerlo manualmente.

## <a name="how-to"></a>Procedimiento

1. Coloque el símbolo de intercalación sobre la interpolación de cadena:

2. Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.

3. Seleccione **Simplificar la interpolación**.

    ![Introducción a la interpolación de cadenas](media/simplify-string-interpolation.png)

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)