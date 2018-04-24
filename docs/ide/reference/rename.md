---
title: Refactorización de cambio de nombre en Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 01/26/2018
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- vs.csharp.refactoring.rename
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 5735203131811b9423cd34f430665fb16a51ad34
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="rename-a-code-symbol-refactoring"></a>Refactorización de cambio de nombre de un símbolo de código

Esta refactorización se aplica a lo siguiente:

- C#

- Visual Basic

**Qué:** Le permite cambiar el nombre de los identificadores de símbolos de código, como campos, variables locales, métodos, espacios de nombres, propiedades y tipos.

**Cuándo:** Desea cambiar con seguridad algo sin tener que buscar todas las instancias y copiar y pegar el nuevo nombre.

**Por qué:** Es probable que copiar y pegar el nuevo nombre en todo un proyecto dé lugar a errores. Esta herramienta de refactorización llevará a cabo con precisión la acción de cambio de nombre.

## <a name="how-to"></a>Procedimiento

1. Resalte o coloque el cursor de texto dentro del elemento cuyo nombre se va a cambiar:

   - C#:

    ![Código resaltado (C#)](media/rename-highlight-cs.png)

   - Visual Basic:

    ![Código resaltado (Visual Basic)](media/rename-highlight-vb.png)

1. A continuación, realice alguno de los siguientes procedimientos:

   - **Teclado**
     - Presione **CTRL+R** y, a continuación, **CTRL+R**. (Tenga en cuenta que su método abreviado de teclado puede ser diferente en función del perfil que haya seleccionado).
   - **Mouse**
     - Seleccione **Editar > Refactorizar > Cambiar nombre**.
     - Haga clic con el botón derecho en el código y seleccione **Cambiar nombre**.

1. Cambie el nombre del elemento escribiendo el nuevo nombre.

   - C#:

    ![Animación del cambio de nombre (C#)](media/rename-animated-cs.gif)

   - Visual Basic:

    ![Cambio de nombre (VB)](media/rename-rename-vb.png)

   > [!TIP]
   > También puede actualizar los comentarios y otras cadenas para que usen este nuevo nombre, así como [obtener una vista previa de los cambios](../../ide/preview-changes.md) antes de guardarlos; para ello, use las casillas del cuadro **Cambiar nombre** que aparece en la parte superior derecha del editor.

1. Cuando esté satisfecho con el cambio, seleccione el botón **Aplicar** o presione **Entrar**. Los cambios se confirmarán.

> [!NOTE]
> Si usa un nombre que ya existe, lo cual produciría un conflicto, el cuadro **Cambiar nombre** se lo advertirá.
>
> ![Conflicto de cambio de nombre](media/rename-conflict-cs.png)

## <a name="see-also"></a>Vea también

[Refactorización](../refactoring-in-visual-studio.md)  
[Vista previa de cambios](../../ide/preview-changes.md)
