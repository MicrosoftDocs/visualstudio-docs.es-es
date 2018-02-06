---
title: "Refactorización de una firma de método en C# | Microsoft Docs"
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
- vs.csharp.refactoring.remove
- vs.csharp.refactoring.reorder
dev_langs: csharp
ms.workload: dotnet
ms.openlocfilehash: 44aaf3f4a570600b715d6d54f5fd80da84611b94
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2018
---
# <a name="change-a-method-signature-in-c"></a>Cambio de firma del método en C# #

**Qué:** Le permite quitar o cambiar el orden de los parámetros de un método.

**Cuándo:** Desea mover o quitar un parámetro de método que se está usando actualmente en diferentes ubicaciones.  

**Por qué:** Podría quitar y cambiar el orden de los parámetros manualmente y, a continuación, buscar todas las llamadas a ese método y cambiarlas una por una, pero esto podría provocar errores.  Esta herramienta de refactorización realizará la tarea automáticamente.

**Cómo**:

1. Resalte o coloque el cursor de texto en el nombre del método para modificar uno de sus usos:

   ![Código resaltado](media/changesignature-highlight-cs.png)

1. A continuación, realice alguno de los siguientes procedimientos:
   * **Teclado**
     * Presione **CTRL+R** y, a continuación, **CTRL+V**.  (Tenga en cuenta que su método abreviado de teclado puede ser diferente en función del perfil que haya seleccionado).
     * Presione **Ctrl +.** para activar el menú **Acciones rápidas y refactorizaciones** y seleccione **Cambiar firma** en el menú emergente de la ventana Vista previa.
   * **Mouse**
     * Seleccione **Editar > Refactorizar > Quitar parámetros**.
     * Seleccione **Editar > Refactorizar > Reordenar parámetros**.
     * Haga clic con el botón derecho en el código, seleccione el menú **Acciones rápidas y refactorizaciones** y elija **Cambiar firma** en el menú emergente de la ventana Vista previa.

1. En el cuadro de diálogo **Cambiar firma** que aparece, puede usar los botones a la derecha para cambiar la firma del método:

   ![Cuadro de diálogo para cambiar firma](media/changesignature-dialog-cs.png)

   | Botón | Description
   | ------ | ---
   | **Up/Down** | Mueve el parámetro seleccionado hacia arriba y hacia abajo en la lista.
   | **Remove**  | Quita el parámetro seleccionado de la lista.
   | **Restore** | Restaura el parámetro seleccionado y tachado a la lista.

   > [!TIP]
   > Use la casilla [**Vista previa de los cambios de referencia**](../../ide/preview-changes.md) para ver cuál será el resultado antes de confirmar.

1. Cuando haya terminado, presione el botón **Aceptar** para realizar los cambios.

   ![Resultado del cambio de firma](media/changesignature-result-cs.png)

## <a name="see-also"></a>Vea también

[Refactorización](../refactoring-in-visual-studio.md)  
[Vista previa de cambios](../../ide/preview-changes.md)