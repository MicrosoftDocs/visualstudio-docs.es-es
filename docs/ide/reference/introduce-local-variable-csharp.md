---
title: "Introducción de una variable local: generación de código (C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 6ba9478c09e55df54f94ed93c7a694f798ae76b4
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/06/2018
---
# <a name="introduce-a-local-variable-in-c"></a>Introducción de una variable local en C# #

**Qué:** Le permite generar de inmediato una variable local para reemplazar una expresión existente.

**Cuándo:** Tiene código que se podría reutilizar con facilidad más adelante si estuviera en una variable local.

**Por qué:** Podría copiar y pegar el código varias veces para usarlo en varias ubicaciones; sin embargo, sería mejor realizar la operación una vez, almacenar el resultado en una variable local y usar esta variable local en todo el proceso.

**Cómo**:

1. Resalte la expresión que desea asignar a una nueva variable local.

   ![Código resaltado](media/local-highlight-cs.png)

1. A continuación, realice alguno de los siguientes procedimientos:
   * **Teclado**
     * Presione **Ctrl +.** para activar el menú **Acciones rápidas y refactorizaciones** y seleccione **Introducir una variable local para todos los casos de "*expresión*"** en el menú emergente de la ventana Vista previa, donde *expresión* es el código que ha destacado.
   * **Mouse**
     * Haga clic con el botón derecho y seleccione el menú **Acciones rápidas y refactorizaciones** y elija **Introducir una variable local para todos los casos de "*expresión*"** en el menú emergente de la ventana Vista previa, donde *expresión* es el código que ha destacado.
     * Haga clic en el botón ![de icono Bombilla](media/bulb-cs.png) que aparece en el margen izquierdo si el cursor de texto ya está en la línea con el subrayado ondulado de color rojo.

   ![Vista previa de la introducción de la variable local](media/local-preview-cs.png)

   > [!TIP]
   > Use el vínculo [**Vista previa de los cambios**](../../ide/preview-changes.md) en la parte inferior de la ventana de vista previa para ver todos los cambios que se aplicarán antes de hacer la selección.

1. La variable local se creará automáticamente con el tipo que se deduce de su uso.  Asigne a la nueva variable local un nuevo nombre escribiéndolo.

   ![Resultado de la introducción de la variable local](media/local-result-cs.png)

   > [!NOTE]
   > Puede usar la opción del menú **...all occurences of...** (...todos los casos de...) para reemplazar todas las instancias de la expresión seleccionada que se encuentren, no solo las que se resalten específicamente.

## <a name="see-also"></a>Vea también

[Generación de código](../code-generation-in-visual-studio.md)  
[Vista previa de cambios](../../ide/preview-changes.md)
