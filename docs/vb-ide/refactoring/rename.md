---
title: "Refactorización - (Visual Basic) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: abf1565b-c7b7-4d45-b3d3-a438a836c70e
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.rename
dev_langs: VB
ms.openlocfilehash: 35313f036e1f324d3f8908a4527cd3a2ad64ae52
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="rename-a-code-symbol-in-visual-basic"></a>Cambiar el nombre de un símbolo de código en Visual Basic
**¿Qué:** le permite cambiar el nombre de los identificadores de símbolos de código, como campos, variables locales, métodos, espacios de nombres, propiedades y tipos.

**Cuándo:** desea cambiar con seguridad algo sin tener que buscar todas las instancias y copiar y pegar el nuevo nombre.  

**Por este motivo:** copiar y pegar el nuevo nombre en todo un proyecto es probable que podría dar lugar a errores.  Esta herramienta de refactorización con precisión llevará a cabo la acción de cambio de nombre.

**Cómo:**

1. Resalte o coloque el cursor de texto dentro del elemento que se va a cambiar:

   ![Código que aparece resaltado](media/rename_highlight.png)

1. A continuación, realice una de las siguientes acciones:
   * **Teclado**
     * Presione **Ctrl + R**, a continuación, **Ctrl + R**.  (Tenga en cuenta que su método abreviado de teclado puede ser diferente en función del perfil que haya seleccionado).
   * **Mouse**
     * Seleccione **Editar > refactorizar > cambiar el nombre de**.
     * Haga clic en el código y seleccione **cambiar el nombre de**.

1. Cambie el nombre del elemento escribiendo el nuevo nombre.

   ![Cambiar el nombre de animación](media/rename_rename.png)

   > [!TIP]
   > También puede actualizar los comentarios y otras cadenas para usar este nuevo nombre, así como [obtener una vista previa de cambios](../../ide/preview-changes.md) antes de guardar, mediante las casillas de verificación en la **cambiar el nombre de** cuadro que aparece en la parte superior derecha de su IDE.

1. Cuando esté satisfecho con el cambio, haga clic en el **aplicar** o presionen **ENTRAR** y los cambios se confirmarán.

> [!NOTE]
> Si utiliza un nombre que ya existe y que se produciría un conflicto, la **cambiar el nombre de** cuadro en el IDE generará una advertencia.
>
> ![Cambiar el nombre de conflictos](media/rename_conflict.png)

## <a name="see-also"></a>Vea también  
[Refactorización (Visual Basic)](../refactoring-vb.md)  
[Vista previa de cambios](../../ide/preview-changes.md)