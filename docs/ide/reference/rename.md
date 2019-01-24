---
title: Refactorización de cambio de nombre
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: a24c8a44cbd7d3c889d92c34c9eac0c5b015be65
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53881015"
---
# <a name="rename-a-code-symbol-refactoring"></a>Refactorización de cambio de nombre de un símbolo de código

Esta refactorización se aplica a lo siguiente:

- C#

- Visual Basic

**Qué:** Permite cambiar el nombre de los identificadores de símbolos de código, como campos, variables locales, métodos, espacios de nombres, propiedades y tipos.

**Cuándo:** Se quiere cambiar con seguridad el nombre de algo sin tener que buscar todas las instancias y copiar y pegar el nombre nuevo.

**Por qué:** Es probable que copiar y pegar el nuevo nombre en todo un proyecto genere errores. Esta herramienta de refactorización llevará a cabo con precisión la acción de cambio de nombre.

## <a name="how-to"></a>Procedimiento

1. Resalte o coloque el cursor de texto dentro del elemento cuyo nombre se va a cambiar:

   - C#:

       ![Código resaltado (C#)](media/rename-highlight-cs.png)

   - Visual Basic:

       ![Código resaltado (Visual Basic)](media/rename-highlight-vb.png)

2. A continuación, realice alguno de los siguientes procedimientos:

   - **Teclado**
      - Presione **CTRL+R** y, a continuación, **CTRL+R**. (Tenga en cuenta que su método abreviado de teclado puede ser diferente en función del perfil que haya seleccionado).
   - **Mouse**
      - Seleccione **Editar > Refactorizar > Cambiar nombre**.
      - Haga clic con el botón derecho en el código y seleccione **Cambiar nombre**.

3. Cambie el nombre del elemento escribiendo el nuevo nombre.

   - C#:

      ![Animación del cambio de nombre (C#)](media/rename-animated-cs.gif)

   - Visual Basic:

      ![Cambio de nombre (VB)](media/rename-rename-vb.png)

   > [!TIP]
   > También puede actualizar los comentarios y otras cadenas para que usen este nuevo nombre, así como [obtener una vista previa de los cambios](../../ide/preview-changes.md) antes de guardarlos; para ello, use las casillas del cuadro **Cambiar nombre** que aparece en la parte superior derecha del editor.

4. Cuando esté satisfecho con el cambio, seleccione el botón **Aplicar** o presione **Entrar**. Los cambios se confirmarán.

> [!NOTE]
> Si usa un nombre que ya existe, lo cual produciría un conflicto, el cuadro **Cambiar nombre** se lo advertirá.
>
> ![Conflicto de cambio de nombre](media/rename-conflict-cs.png)

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
- [Vista previa de cambios](../../ide/preview-changes.md)
