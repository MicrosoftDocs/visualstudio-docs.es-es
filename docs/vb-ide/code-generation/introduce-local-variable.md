---
title: "Introducir una variable local - generación de código (Visual Basic) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1490d6ac-ed56-4d03-95db-c23f23cba70d
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 67302893dbebb65316b9c2aab09f70ddaa3e6567
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="introduce-a-local-variable-in-visual-basic"></a>Introducir una variable local en Visual Basic
**¿Qué:** permite generar inmediatamente una variable local para reemplazar una expresión existente.

**Cuándo:** tiene código que se puede reutilizar con facilidad más adelante si estuviera en una variable local.  

**Por este motivo:** podría copiar y pegar el código varias veces para usarlo en varias ubicaciones, sin embargo, sería mejor realizar la operación una vez, almacena el resultado en una variable local y use la throughought de variable local. 

**Cómo:**

1. Resalte la expresión que desea asignar a una nueva variable local.

   ![Código que aparece resaltado](media/local_highlight.png)

1. A continuación, realice una de las siguientes acciones:
   * **Teclado**
     * Presione **Ctrl +.** Para activar el **acciones rápidas y refactorizaciones** menú y seleccione  **introducir variables locales (todas las apariciones de) '*expresión*' ** desde la ventana emergente la ventana de vista previa, donde *expresión* es el código resaltado.
   * **Mouse**
     * Haga clic en y seleccione el **acciones rápidas y refactorizaciones** menú y seleccione  **introducir variables locales (todas las apariciones de) '*expresión*' ** desde la ventana emergente la ventana de vista previa, donde *expresión* es el código resaltado.
     * Haga clic en el botón ![Bombilla](media/bulb.png) icono que aparece en el margen izquierdo si el cursor de texto ya está en la línea con la línea roja ondulada.

   ![Presentar la vista previa local](media/local_preview.png)

   >[!TIP]
   >Use la [ **obtener una vista previa de cambios** ](../../ide/preview-changes.md) vínculo en la parte inferior de la ventana de vista previa para ver todos los cambios que se realizarán antes de realizar la selección.

1. La variable local se creará automáticamente con el tipo deducido de su uso.  Asigne un nuevo nombre de la variable local nueva escribiéndola de nuevo.

   ![Introducir resultado local](media/local_result.png)

   >[!NOTE]
   >Puede usar el **.. preseleccionan todos repeticiones de...**  opción de menú para reemplazar todas las instancias de la expresión seleccionada se encuentra, no sólo a aquél resaltado específicamente.

## <a name="see-also"></a>Vea también  
[Code Generation (Visual Basic)](../code-generation-vb.md) (Generación de código (Visual Basic))  
[Vista previa de cambios](../../ide/preview-changes.md) 