---
title: Cambiar signatura del método
description: Elimine o cambie el orden de los parámetros de un método. Haga clic con el botón derecho en el método, seleccione Acciones rápidas y refactorizaciones y, luego, Cambiar firma.
ms.date: 01/26/2018
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
ms.openlocfilehash: 97c03c798732b5d722b2dc49f3ec7ffa490b4f06
ms.sourcegitcommit: 3e74ec49a54e5c3da7631f4466128cdf4384af6b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2019
ms.locfileid: "68711261"
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

   ![Cuadro de diálogo para cambiar firma](media/changesignature-dialog-cs.png)

   | Botón | DESCRIPCIÓN
   | ------ | ---
   | **Up/Down** | Mueve el parámetro seleccionado hacia arriba y hacia abajo en la lista.
   | **Remove** | Quita el parámetro seleccionado de la lista.
   | **Restore** | Restaura el parámetro seleccionado y tachado a la lista.

   > [!TIP]
   > Use la casilla **Vista previa de los cambios de referencia** para [ver cuál será el resultado antes de confirmar](../../ide/preview-changes.md).

4. Cuando haya terminado, presione el botón **Aceptar** para realizar los cambios.

   - C#:

      ![Resultado del cambio de firma (C#)](media/changesignature-result-cs.png)

   - Visual Basic:

      ![Resultado del cambio de firma (Visual Basic)](media/changesignature-result-vb.png)

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
- [Vista previa de cambios](../../ide/preview-changes.md)