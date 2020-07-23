---
title: Cambiar signatura del método
description: Agregue, quite o cambie el orden de los parámetros de un método. Haga clic con el botón derecho en el método, seleccione Acciones rápidas y refactorizaciones y, luego, Cambiar firma.
ms.date: 07/20/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.remove
- vs.csharp.refactoring.reorder
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 2d91406b65950515afb3659c0d5918841465b2fc
ms.sourcegitcommit: 363f3e6e30dd54366ade0d08920755da5951535c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/21/2020
ms.locfileid: "86869573"
---
# <a name="change-a-method-signature-refactoring"></a>Refactorización de cambio de una firma de método

Esta refactorización se aplica a lo siguiente:

- C#

- Visual Basic

**Qué:** Permite quitar o cambiar el orden de los parámetros de un método.

**Cuándo:** Se quiere mover o quitar un parámetro de método que se está usando actualmente en diferentes ubicaciones.

**Por qué:** Se podría quitar y cambiar el orden de los parámetros manualmente y, después, buscar todas las llamadas a ese método y cambiarlas una por una, pero esto podría provocar errores.  Esta herramienta de refactorización realizará la tarea automáticamente.

## <a name="how-to"></a>Procedimiento

1. Resalte o coloque el cursor de texto en el nombre del método para modificar uno de sus usos:

   - C#:

       ![Código resaltado (C#)](media/changesignature-highlight-cs.png)

   - VB:

       ![Código resaltado (Visual Basic)](media/changesignature-highlight-vb.png)

2. A continuación, realice alguno de los siguientes procedimientos:

   - **Teclado**
      - Presione **CTRL+R** y, a continuación, **CTRL+V**.  (Tenga en cuenta que su método abreviado de teclado puede ser diferente en función del perfil que haya seleccionado).
      - Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones** y seleccione **Cambiar firma** en el menú emergente de la ventana Vista previa.
   - **Mouse**
      - Seleccione **Editar > Refactorizar > Quitar parámetros**.
      - Seleccione **Editar > Refactorizar > Reordenar parámetros**.
      - Haga clic con el botón derecho en el código, seleccione el menú **Acciones rápidas y refactorizaciones** y elija **Cambiar firma** en el menú emergente de la ventana Vista previa.

3. En el cuadro de diálogo **Cambiar firma** que aparece, puede usar los botones a la derecha para cambiar la firma del método:

   ![Cuadro de diálogo para cambiar firma](media/change-signature.png)

   | Botón | Descripción
   | ------ | ---
   | **Up/Down** | Mueve el parámetro seleccionado hacia arriba y hacia abajo en la lista.
   | **Add** | Agrega un parámetro nuevo a la lista
   | **Remove** | Quita el parámetro seleccionado de la lista.
   | **Restore** | Restaura el parámetro seleccionado y tachado a la lista.

   > [!TIP]
   > Use la casilla **Vista previa de los cambios de referencia** para [ver cuál será el resultado antes de confirmar](../../ide/preview-changes.md).

4. Al seleccionar **Agregar** en el cuadro de diálogo **Cambiar firma**, se abrirá el cuadro de diálogo **Agregar parámetro**. que permite agregar un nombre de tipo y un nombre de parámetro. Puede optar por hacer que el parámetro sea obligatorio u opcional con un valor predeterminado. Tras ello, puede agregar un valor en el sitio de llamada y elegir un argumento con nombre para ese valor, o bien introducir una variable TODO. La variable TODO coloca un elemento TODO en el código para recorrer cada error y pasar por cada sitio de llamada de manera independiente y decidir qué omitir y qué no. En el caso de los parámetros opcionales, existe la opción de omitir el sitio de llamada por completo.

    ![Cuadro de diálogo Agregar parámetro: C#](media/add-parameter-dialog.png)

5. Cuando haya terminado de agregar un parámetro, presione el botón **Aceptar** para obtener una vista previa de los cambios.

    ![Cuadro de diálogo para cambiar firma](media/change-signature.png)

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
- [Vista previa de cambios](../../ide/preview-changes.md)