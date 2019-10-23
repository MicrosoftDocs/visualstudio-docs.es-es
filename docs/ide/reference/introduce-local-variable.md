---
title: Introducción de una variable local
description: Genere una variable local para reemplazar una expresión existente. Seleccione la expresión, haga clic con el botón derecho y seleccione el menú Acciones rápidas y refactorizaciones y seleccione Introducir una variable local para todos los casos de "expresión".
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 6407810b4143d5edacecf42990ae5b6d63497be2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668755"
---
# <a name="introduce-a-local-variable-in-visual-studio"></a>Introducción de una variable local en Visual Basic

Esta generación de código se aplica a:

- C#

- Visual Basic

**Qué:** Permite generar de inmediato una variable local para reemplazar una expresión existente.

**Cuándo:** Se tiene código que se podría reutilizar con facilidad más adelante si estuviera en una variable local.

**Por qué:** Se podría copiar y pegar el código varias veces para usarlo en varias ubicaciones, pero sería mejor realizar la operación una vez, almacenar el resultado en una variable local y usarla en todo el proceso.

## <a name="how-to"></a>Procedimiento

1. Resalte la expresión que desea asignar a una nueva variable local.

   - C#:

       ![Código resaltado (C#)](media/local-highlight-cs.png)

   - Visual Basic:

       ![Código resaltado (VB)](media/local-highlight-vb.png)

2. A continuación, realice alguno de los siguientes procedimientos:

   - **Teclado**
      - Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.
   - **Mouse**
      - Haga clic con el botón derecho y seleccione el menú **Acciones rápidas y refactorizaciones**.
      - Haga clic en el botón ![icono de destornillador](media/screwdriver.png) que aparece en el margen izquierdo si el cursor de texto ya está en la línea con la expresión resaltada.

   ![Vista previa de la introducción de la variable local](media/local-preview-cs.png)

3. Seleccione **Introducir la variable local para todas las repeticiones de "expresión"** en el menú desplegable.

   > [!TIP]
   > Use el vínculo **Vista previa de los cambios** en la parte inferior de la ventana de vista previa [para ver todos los cambios ](../../ide/preview-changes.md) que se aplicarán antes de realizar la selección.

   La variable local se crea con el tipo que se deduce de su uso. Dé a la nueva variable local un nombre nuevo.

   - C#:

       ![Resultado de implementación de interfaz (C#)](media/local-result-cs.png)

   - Visual Basic:

       ![Resultado de implementación de interfaz (VB)](media/local-result-vb.png)

   > [!NOTE]
   > La opción de menú **...para todas las repeticiones de...** puede servir para reemplazar todas las instancias de la expresión seleccionada que se encuentren, no solo las que se resalten específicamente.

## <a name="see-also"></a>Vea también

- [Generación de código](../code-generation-in-visual-studio.md)
- [Vista previa de cambios](../../ide/preview-changes.md)