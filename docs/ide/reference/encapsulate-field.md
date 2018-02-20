---
title: "Refactorización de un campo a una propiedad en Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- vs.csharp.refactoring.encapsulatefield
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 78d2c33002e59eab1b6e8605092a74d9995453a8
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="encapsulate-a-field-refactoring"></a>Refactorización de encapsulamiento de un campo

Esta refactorización se aplica a lo siguiente:

- C#

- Visual Basic

**Qué:** Le permite convertir un campo en una propiedad y actualizar todos los usos de ese campo para utilizar la propiedad recién creada.

**Cuándo:** Desea mover un campo a una propiedad y actualizar todas las referencias a ese campo.

**Por qué:** Desea proporcionar acceso de otras clases a un campo, pero no desea que esas clases tengan acceso directo.  Al encapsular el campo en una propiedad, puede escribir código para comprobar el valor que se está asignando, por ejemplo.

## <a name="how-to"></a>Procedimiento

1. Resalte o coloque el cursor de texto en el nombre del campo que se va a encapsular:

   - C#:

    ![Código resaltado (C#)](media/encapsulate-highlight-cs.png)

   - Visual Basic:

    ![Código resaltado (Visual Basic)](media/encapsulate-highlight-vb.png)

1. A continuación, realice alguno de los siguientes procedimientos:

   - **Teclado**
     - Presione **CTRL+R** y, a continuación, **CTRL+E**.  (Tenga en cuenta que su método abreviado de teclado puede ser diferente en función del perfil que haya seleccionado).
     - Presione **Ctrl +.** para activar el menú **Acciones rápidas y refactorizaciones** y seleccione la entrada **Encapsular campo** en el menú emergente de la ventana Vista previa.
   - **Mouse**
     - Seleccione **Editar > Refactorizar > encapsular campo**.
     - Haga clic con el botón derecho en el código, seleccione el menú **Acciones rápidas y refactorizaciones** y elija la entrada **Encapsular campo** en el menú emergente de la ventana Vista previa.

   Selección | Description
   --------- | -----------
   **Encapsular campo (y usar propiedad)** | Encapsula el campo con una propiedad y actualiza todos los usos del campo para utilizar la propiedad generada
   **Encapsular campo (pero seguir usando el campo)** | Encapsula el campo con una propiedad, pero deja intactos todos los usos del campo

   La propiedad se crea y se actualizan las referencias al campo, si se han seleccionado.

   > [!TIP]
   > Use el vínculo **Vista previa de los cambios** de la ventana emergente [para ver cuál será el resultado](../../ide/preview-changes.md) antes de confirmar.

   - C#:

    ![Resultado de encapsulamiento de la propiedad (C#)](media/encapsulate-result-cs.png)

   - Visual Basic:

    ![Resultado de encapsulamiento de la propiedad (Visual Basic)](media/encapsulate-result-vb.png)

## <a name="see-also"></a>Vea también

[Refactorización](../refactoring-in-visual-studio.md)  
[Vista previa de cambios](../../ide/preview-changes.md)