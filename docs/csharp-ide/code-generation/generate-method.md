---
title: "Generar un método: generación de código (C#) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 683790b4-b68b-42d7-8dc4-a68eca05aa01
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 2d0354549d01fb31a813630066c96f6378db4b7a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="generate-a-method-in-c"></a>Generar un método en C# #
**¿Qué:** le permite agregar inmediatamente un método a una clase. 

**Cuándo:** introducir un nuevo método y desea correctamente, declare automáticamente.  

**Por este motivo:** podría declarar el método y los parámetros antes de usarlo, sin embargo, esta característica generará automáticamente la declaración. 

**Cómo:**

1. Coloque el cursor en la línea donde hay un subrayado ondulado de color rojo que indica que ha usado un método que no existe todavía.

   ![Código que aparece resaltado](media/method_highlight.png)

1. A continuación, realice una de las siguientes acciones:
   * **Teclado**
     * Presione **Ctrl +.** Para activar el **acciones rápidas y refactorizaciones** menú y seleccione **generar método** desde la ventana emergente de ventana de vista previa.
   * **Mouse**
     * Haga clic en y seleccione el **acciones rápidas y refactorizaciones** menú y seleccione **generar método** desde la ventana emergente de ventana de vista previa.
     * Mantenga el mouse sobre el subrayado ondulado de color rojo y haga clic en el ![Bombilla](media/bulb.png) icono que aparece.
     * Haga clic en el botón ![Bombilla](media/bulb.png) icono que aparece en el margen izquierdo si el cursor de texto ya está en la línea con la línea roja ondulada.

   ![Generar vista previa (método)](media/method_preview.png)

   >[!TIP]
   >Use la [ **obtener una vista previa de cambios** ](../../ide/preview-changes.md) vínculo en la parte inferior de la ventana de vista previa para ver todos los cambios que se realizarán antes de realizar la selección.

1. El método se creará automáticamente con los parámetros que se deduce de su uso.

   ![Generar el resultado del método](media/method_result.png)

## <a name="see-also"></a>Vea también  
[Code Generation (C#)](../code-generation-csharp.md) (Generación de código (C#))  
[Vista previa de cambios](../../ide/preview-changes.md)
