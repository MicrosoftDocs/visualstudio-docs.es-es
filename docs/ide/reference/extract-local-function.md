---
title: Extraer función local
description: Convierta un fragmento de código en su propia función; para ello, seleccione el código y escriba Ctrl+R y Ctrl+M.
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 80ac8f23b5404d70b70166915cd791f2c0d7ed07
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860976"
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

    ![Captura de pantalla de la ventana de código de Visual Studio con una línea resaltada. El menú Acciones rápidas y refactorizaciones está abierto y la opción Extraer función local está seleccionada.](media/extract-local-function.png)

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
- [Vista previa de cambios](../../ide/preview-changes.md)
