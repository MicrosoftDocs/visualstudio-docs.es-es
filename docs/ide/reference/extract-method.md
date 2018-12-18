---
title: Extracción de un método en Visual Studio
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- vs.csharp.refactoring.extractmethod
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 6978457fdc976f87a8334b181ab69dfd78ef240c
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2018
ms.locfileid: "51294545"
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

       ![Código resaltado (C#)](media/extractmethod-highlight-cs.png)

   - Visual Basic:

       ![Código resaltado (Visual Basic)](media/extractmethod-highlight-vb.png)

2. A continuación, realice alguno de los siguientes procedimientos:

   - **Teclado**
      - Presione **CTRL+R** y, a continuación, **CTRL+M**. (Tenga en cuenta que su método abreviado de teclado puede ser diferente en función del perfil que haya seleccionado).
      - Presione **Ctrl**+**.** para activar el menú **Acciones rápidas y refactorizaciones** y seleccione **Extraer método** en el menú emergente de la ventana Vista previa.
   - **Mouse**
      - Seleccione **Editar > Refactorizar > Extraer método**.
      - Haga clic con el botón derecho en el código y seleccione **Refactorizar > Extraer > Extraer método**.
      - Haga clic con el botón derecho en el código, seleccione el menú **Acciones rápidas y refactorizaciones** y elija **Extraer método** en el menú emergente de la ventana Vista previa.

   El método se creará de inmediato. Desde aquí, ahora puede cambiar el nombre del método simplemente escribiendo el nuevo nombre.

   > [!TIP]
   > También puede actualizar los comentarios y demás cadenas para que usen este nuevo nombre, así como [obtener una vista previa de los cambios](../../ide/preview-changes.md) antes de guardar, con las casillas del cuadro **Cambiar nombre** que aparece en la parte superior derecha del IDE.

   - C#:

      ![Cambio de nombre del método (C#)](media/extractmethod-rename-cs.png)

   - Visual Basic:

      ![Cambio de nombre del método (Visual Basic)](media/extractmethod-rename-vb.png)

3. Cuando esté satisfecho con el cambio, seleccione el botón **Aplicar** o presione **Entrar**. Los cambios se confirmarán.

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
- [Vista previa de cambios](../../ide/preview-changes.md)