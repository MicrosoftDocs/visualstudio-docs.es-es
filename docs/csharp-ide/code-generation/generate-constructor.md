---
title: "Generar un constructor - generación de código (C#) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2280cfa-a9ec-4b56-9d94-c8fd384db980
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 31b0a187e0640a94d9401a1e20fd03d81ff5b920
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="generate-a-constructor-in-c"></a>Generar un constructor en C# #
**¿Qué:** le permite generar inmediatamente el código para un nuevo constructor en una clase. 

**Cuándo:** introducir un nuevo constructor y desea correctamente, declare automáticamente.  

**Por este motivo:** podría declarar el constructor antes de usarlo, sin embargo, esta característica generará, con los parámetros adecuados, automáticamente. 

**Cómo:**

1. Coloque el cursor en la línea donde hay un subrayado ondulado de color rojo que indica que ha utilizado un constructor que aún no existe.

   ![Código que aparece resaltado](media/constructor_highlight.png)

1. A continuación, realice una de las siguientes acciones:
   * **Teclado**
     * Presione **Ctrl +.** Para activar el **acciones rápidas y refactorizaciones** menú y seleccione  **generar constructor en '*TypeName*' ** desde la ventana emergente de ventana de vista previa.
   * **Mouse**
     * Haga clic en y seleccione el **acciones rápidas y refactorizaciones** menú y seleccione  **generar constructor en '*TypeName*' ** desde la ventana emergente de ventana de vista previa.
     * Mantenga el mouse sobre el subrayado ondulado de color rojo y haga clic en el ![Bombilla](media/bulb.png) icono que aparece.
     * Haga clic en el botón ![Bombilla](media/bulb.png) icono que aparece en el margen izquierdo si el cursor de texto ya está en la línea con la línea roja ondulada.

   ![Generar vista previa de constructor](media/constructor_preview.png)

   >[!TIP]
   >Use la [ **obtener una vista previa de cambios** ](../../ide/preview-changes.md) vínculo en la parte inferior de la ventana de vista previa para ver todos los cambios que se realizarán antes de realizar la selección.

1. El constructor se creará automáticamente con los parámetros que se deduce de su uso.

   ![Generar el resultado del constructor](media/constructor_result.png)
  
## <a name="see-also"></a>Vea también  
[Code Generation (C#)](../code-generation-csharp.md) (Generación de código (C#))  
[Vista previa de cambios](../../ide/preview-changes.md)