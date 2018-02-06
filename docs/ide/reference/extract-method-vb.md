---
title: "Extracción de un método en Visual Basic | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.extractmethod
dev_langs: VB
ms.workload: multiple
ms.openlocfilehash: f9e55a41f9a61626e8fce18cb11da6edc8a8bced
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2018
---
# <a name="extract-a-method-in-visual-basic"></a>Extracción de un método en Visual Basic

**Qué:** Le permite convertir un fragmento de código en su propio método.

**Cuándo:** Tiene un fragmento de código existente en algún método que debe llamarse desde otro método.  

**Por qué:** Podría copiar y pegar ese código, pero esto provocaría una duplicación.  Una mejor solución consiste en refactorizar ese fragmento en su propio método al que cualquier otro método puede llamar libremente.

**Cómo**:

1. Resalte el código que se va a extraer:

   ![Código resaltado](media/extractmethod-highlight-vb.png)

1. A continuación, realice alguno de los siguientes procedimientos:
   * **Teclado**
     * Presione **CTRL+R** y, a continuación, **CTRL+M**.  (Tenga en cuenta que su método abreviado de teclado puede ser diferente en función del perfil que haya seleccionado).
     * Presione **Ctrl +.** para activar el menú **Acciones rápidas y refactorizaciones** y seleccione **Extraer método** en el menú emergente de la ventana Vista previa.
   * **Mouse**
     * Seleccione **Editar > Refactorizar > Extraer método**.
     * Haga clic con el botón derecho en el código y seleccione **Refactorizar > Extraer > Extraer método**.
     * Haga clic con el botón derecho en el código, seleccione el menú **Acciones rápidas y refactorizaciones** y elija **Extraer método** en el menú emergente de la ventana Vista previa.

   El método se creará de inmediato.  Desde aquí, ahora puede cambiar el nombre del método simplemente escribiendo el nuevo nombre.

   > [!TIP]
   > También puede actualizar los comentarios y otras cadenas para que usen este nuevo nombre, así como [obtener una vista previa de los cambios](../../ide/preview-changes.md) antes de guardar, mediante las casillas de del cuadro **Cambiar nombre** que aparece en la parte superior derecha de su IDE.

   ![Cambio de nombre del método](media/extractmethod-rename-vb.png)

1. Cuando esté satisfecho con el cambio, haga clic en el botón **Aplicar** o presione **Entrar** y los cambios se confirmarán.

## <a name="see-also"></a>Vea también

[Refactorización](../refactoring-in-visual-studio.md)  
[Vista previa de cambios](../../ide/preview-changes.md)