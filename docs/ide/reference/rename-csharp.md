---
title: "Cambio de nombre de refactorización en Visual Studio para C# | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- vs.csharp.refactoring.rename
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: e1325de81e16b0e381f07af4d8073d0a3fa4330c
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/06/2018
---
# <a name="rename-a-code-symbol-in-c"></a>Cambio de nombre de un símbolo de código en C# #

**Qué:** Le permite cambiar el nombre de los identificadores de símbolos de código, como campos, variables locales, métodos, espacios de nombres, propiedades y tipos.

**Cuándo:** Desea cambiar con seguridad algo sin tener que buscar todas las instancias y copiar y pegar el nuevo nombre.

**Por qué:** Es probable que copiar y pegar el nuevo nombre en todo un proyecto dé lugar a errores.  Esta herramienta de refactorización llevará a cabo con precisión la acción de cambio de nombre.

**Cómo**:

1. Resalte o coloque el cursor de texto dentro del elemento cuyo nombre se va a cambiar:

   ![Código resaltado](media/rename-highlight-cs.png)

1. A continuación, realice alguno de los siguientes procedimientos:
   * **Teclado**
     * Presione **CTRL+R** y, a continuación, **CTRL+R**. (Tenga en cuenta que su método abreviado de teclado puede ser diferente en función del perfil que haya seleccionado).
   * **Mouse**
     * Seleccione **Editar > Refactorizar > Cambiar nombre**.
     * Haga clic con el botón derecho en el código y seleccione **Cambiar nombre**.

1. Cambie el nombre del elemento escribiendo el nuevo nombre.

   ![Animación del cambio de nombre](media/rename-animated-cs.gif)

   > [!TIP]
   > También puede actualizar los comentarios y otras cadenas para que usen este nuevo nombre, así como [obtener una vista previa de los cambios](../../ide/preview-changes.md) antes de guardar, mediante las casillas de del cuadro **Cambiar nombre** que aparece en la parte superior derecha de su IDE.

1. Cuando esté satisfecho con el cambio, haga clic en el botón **Aplicar** o presione **Entrar** y los cambios se confirmarán.

> [!NOTE]
> Si utiliza un nombre que ya existe, lo cual produciría un conflicto, el cuadro **Cambiar nombre** de su IDE se lo advertirá.
>
> ![Conflicto de cambio de nombre](media/rename-conflict-cs.png)

## <a name="see-also"></a>Vea también

[Refactorización](../refactoring-in-visual-studio.md)  
[Vista previa de cambios](../../ide/preview-changes.md)
