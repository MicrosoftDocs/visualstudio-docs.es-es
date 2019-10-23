---
title: Refactorización de cambio de nombre
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.rename
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 2991227b3c8d742da360465e6c506e7123259e2c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655621"
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

## <a name="remarks"></a>Comentarios

- A partir de la versión 16.3 de Visual Studio 2019, cuando se cambia el nombre de un tipo que coincide con el nombre del archivo en el que se encuentra, aparece una casilla que permite cambiar el nombre del archivo al mismo tiempo. Esta opción aparece cuando se cambia el nombre de una clase, una interfaz o una enumeración. No es compatible con los tipos parciales con varias definiciones.

   ![Animación del cambio de nombre con un archivo en C#](media/rename-with-file-animated-cs.gif)

- Si usa un nombre que ya existe, lo cual produciría un conflicto, el cuadro **Cambiar nombre** se lo advertirá.

   ![Conflicto de cambio de nombre](media/rename-conflict-cs.png)

- Otra manera de cambiar el nombre de un símbolo es cambiar su nombre en el editor. A continuación, con el cursor en el nombre del símbolo, presione **Ctrl**+ **.** o simplemente expanda el menú de icono de bombilla que aparece y elija **Cambiar nombre\<nombre antiguo> a \<nombre nuevo>** .

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
- [Vista previa de cambios](../../ide/preview-changes.md)
