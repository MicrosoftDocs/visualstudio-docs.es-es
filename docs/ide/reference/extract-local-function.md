---
title: Extraer función local
description: Convierta un fragmento de código en su propia función; para ello, seleccione el código y escriba Ctrl+R y Ctrl+M.
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: e007246b85671a0f4606bbdb3d1e9c4e0dc83541
ms.sourcegitcommit: cd7f122c6850cf442a4ca42d51d05c7a8fe9038d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/12/2021
ms.locfileid: "98129463"
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
