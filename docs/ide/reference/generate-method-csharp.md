---
title: "Generación de un método: generación de código (C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 683790b4-b68b-42d7-8dc4-a68eca05aa01
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: e4caf80bec38305613111f290b80eafb74547598
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/06/2018
---
# <a name="generate-a-method-in-c"></a>Generación de un método en C# #
**Qué:** Le permite agregar inmediatamente un método a una clase. 

**Cuándo:** Introduce un nuevo método y desea declararlo de manera adecuada y de inmediato.  

**Por qué:** Podría declarar el método y los parámetros antes de usarlo; sin embargo, esta característica generará la declaración automáticamente. 

**Cómo**:

1. Coloque el cursor en la línea donde hay un subrayado ondulado de color rojo que indica que ha utilizado un método que aún no existe.

   ![Código resaltado](media/method-highlight-cs.png)

1. A continuación, realice alguno de los siguientes procedimientos:
   * **Teclado**
     * Presione **Ctrl +.** para activar el menú **Acciones rápidas y refactorizaciones** y seleccione **Generar método** en el menú emergente de la ventana Vista previa.
   * **Mouse**
     * Haga clic con el botón derecho y seleccione el menú **Acciones rápidas y refactorizaciones** y elija **Generar método** en el menú emergente de la ventana Vista previa.
     * Mantenga el mouse sobre el subrayado ondulado de color rojo y haga clic en el botón ![de icono Bombilla](media/bulb-cs.png) que aparece.
     * Haga clic en el botón ![de icono Bombilla](media/bulb-cs.png) que aparece en el margen izquierdo si el cursor de texto ya está en la línea con el subrayado ondulado de color rojo.

   ![Vista previa de la generación de método](media/method-preview-cs.png)

   >[!TIP]
   >Use el vínculo [**Vista previa de los cambios**](../../ide/preview-changes.md) en la parte inferior de la ventana de vista previa para ver todos los cambios que se aplicarán antes de hacer la selección.

1. El método se creará automáticamente con los parámetros que se deducen de su uso.

   ![Resultado de la generación de método](media/method-result-cs.png)

## <a name="see-also"></a>Vea también

[Generación de código](../code-generation-in-visual-studio.md)  
[Vista previa de cambios](../../ide/preview-changes.md)
