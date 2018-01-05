---
title: "Firma de método de cambio - refactorización (C#) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: b4f45f9d-9c8f-46ae-99f7-7705c6d90b6e
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- vs.csharp.refactoring.remove
- vs.csharp.refactoring.reorder
dev_langs: csharp
ms.workload: dotnet
ms.openlocfilehash: 6344a30b5772ffa23c09baa4f38a4478d907cc9e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="change-a-method-signature-in-c"></a>Cambiar una firma de método en C# #
**¿Qué:** permite quitar o cambiar el orden de los parámetros del método.

**Cuándo:** que desea mover o quitar un parámetro de método que se está usando actualmente en diferentes ubicaciones.  

**Por este motivo:** podría manualmente quitar y cambiar el orden de los parámetros y, a continuación, buscar todas las llamadas a ese método y cambiarlos uno por uno, pero que puede provocar errores.  Esta herramienta refactorización realizará la tarea automáticamente.

**Cómo:**

1. Resalte o coloque el cursor de texto en el nombre del método para modificar o uno de sus usos:

   ![Código que aparece resaltado](media/changesignature_highlight.png)

1. A continuación, realice una de las siguientes acciones:
   * **Teclado**
     * Presione **Ctrl + R**, a continuación, **Ctrl + V**.  (Tenga en cuenta que su método abreviado de teclado puede ser diferente en función del perfil que haya seleccionado).
     * Presione **Ctrl +.** Para activar el **acciones rápidas y refactorizaciones** menú y seleccione **Cambiar firma** desde la ventana emergente de ventana de vista previa.
   * **Mouse**
     * Seleccione **Editar > refactorizar > Quitar parámetros**.
     * Seleccione **Editar > refactorizar > Reordenar parámetros**.
     * Haga clic en el código, seleccione la **acciones rápidas y refactorizaciones** menú y seleccione **Cambiar firma** desde la ventana emergente de ventana de vista previa.

1. En el **Cambiar firma** cuadro de diálogo que aparece, puede usar los botones a la derecha para cambiar la firma del método:

   ![Cuadro de diálogo de firma de cambio](media/changesignature_dialog.png)

   | Botón | Descripción
   | ------ | ---
   | **Arriba/abajo** | Mueve el parámetro seleccionado y Bajar la lista
   | **Remove**  | Quita el parámetro seleccionado en la lista
   | **Restaurar** | Restaurar el parámetro seleccionado, tachado en la lista

   > [!TIP]
   > Use la [ **vista previa de cambios de referencia** ](../../ide/preview-changes.md) casilla de verificación para ver cuál será el resultado antes de confirmar a él.

1. Cuando haya terminado, presione el **Aceptar** botón para realizar los cambios.

   ![Resultado de cambio de firma](media/changesignature_result.png)

## <a name="see-also"></a>Vea también  
[Refactorización (C#)](../refactoring-csharp.md)  
[Vista previa de cambios](../../ide/preview-changes.md)