---
title: Extracción de un método
description: Convierta un fragmento de código en su propio método; para ello, seleccione el código y escriba Ctrl+R, Ctrl+M.
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.extractmethod
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 21f6ac868268c40ea6df837596546f86fd9a3a44
ms.sourcegitcommit: cd7f122c6850cf442a4ca42d51d05c7a8fe9038d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/12/2021
ms.locfileid: "98129476"
---
# <a name="extract-a-method-refactoring"></a>Refactorización de extracción de un método

Esta refactorización se aplica a lo siguiente:

- C#

- Visual Basic

**Qué:** Le permite convertir un fragmento de código en su propio método.

**Cuándo:** Tiene un fragmento de código existente en algún método que debe llamarse desde otro método.

**Por qué:** Podría copiar y pegar ese código, pero esto provocaría una duplicación. Una mejor solución consiste en refactorizar ese fragmento en su propio método al que cualquier otro método puede llamar libremente.

## <a name="how-to"></a>Procedimiento

1. Resalte el código que se va a extraer:

   - C#:

       Captura de pantalla en la que se muestra código de C# para la clase Program. En la función Main de esa clase, aparece resaltada una línea de código.](media/extractmethod-highlight-cs.png)

   - Visual Basic:

       ![Captura de pantalla en la que muestra el código de Visual Basic del procedimiento Main Sub. En ese procedimiento, se resalta una línea de código.](media/extractmethod-highlight-vb.png)

2. A continuación, realice alguno de los siguientes procedimientos:

   - **Teclado**
      - Presione **CTRL+R** y, a continuación, **CTRL+M**. (Tenga en cuenta que su método abreviado de teclado puede ser diferente en función del perfil que haya seleccionado).
      - Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones** y seleccione **Extraer método** en el menú emergente de la ventana Vista previa.
   - **Mouse**
      - Seleccione **Editar > Refactorizar > Extraer método**.
      - Haga clic con el botón derecho en el código y seleccione **Refactorizar > Extraer > Extraer método**.
      - Haga clic con el botón derecho en el código, seleccione el menú **Acciones rápidas y refactorizaciones** y elija **Extraer método** en el menú emergente de la ventana Vista previa.

   El método se creará de inmediato. Desde aquí, ahora puede cambiar el nombre del método simplemente escribiendo el nuevo nombre.

   > [!TIP]
   > También puede actualizar los comentarios y demás cadenas para que usen este nuevo nombre, así como [obtener una vista previa de los cambios](../../ide/preview-changes.md) antes de guardar, con las casillas del cuadro **Cambiar nombre** que aparece en la parte superior derecha del IDE.

   - C#:

      ![Captura de pantalla en la que se muestra código de C# para la clase Program. Se resalta el nombre de un método y aparece la ventana emergente Cambiar nombre.](media/extractmethod-rename-cs.png)

   - Visual Basic:

      ![Captura de pantalla en la que muestra el código de Visual Basic del procedimiento Main Sub. Se resalta el nombre de un método y aparece la ventana emergente Cambiar nombre.](media/extractmethod-rename-vb.png)

3. Cuando esté satisfecho con el cambio, seleccione el botón **Aplicar** o presione **Entrar**. Los cambios se confirmarán.

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
- [Vista previa de cambios](../../ide/preview-changes.md)
