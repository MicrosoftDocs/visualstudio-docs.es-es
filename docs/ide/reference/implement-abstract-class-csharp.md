---
title: "Implementación de una clase abstracta: generación de código (C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96cfed7f-f090-4369-8a85-2dcd4c7cf12b
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: f089ffbe33d4a36e84d6d39abb3b3db3c4b2aeb7
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2018
---
# <a name="implement-an-abstract-class-in-c"></a>Implementación de una clase abstracta en C# #
**Qué:** Le permite generar inmediatamente el código necesario para implementar una clase abstracta. 

**Cuándo:** Desea heredar de una clase abstracta.  

**Por qué:** Podría implementar manualmente todos los miembros abstractos uno por uno, sin embargo, esta característica generará automáticamente todas las firmas de método de manera automática. 

**Cómo**:

1. Coloque el cursor en la línea donde hay un subrayado ondulado de color rojo que indica que ha heredado de una clase abstracta pero no ha implementado todos los miembros requeridos.

   ![Código resaltado](media/abstract-highlight-cs.png)

1. A continuación, realice alguno de los siguientes procedimientos:
   * **Teclado**
     * Presione **Ctrl +.** para activar el menú **Acciones rápidas y refactorizaciones** y seleccione **Implementar clase abstracta** en el menú emergente de la ventana Vista previa.
   * **Mouse**
     * Haga clic con el botón derecho y seleccione el menú **Acciones rápidas y refactorizaciones** y elija **Implementar clase abstracta** en el menú emergente de la ventana Vista previa.
     * Mantenga el mouse sobre el subrayado ondulado de color rojo y haga clic en el botón ![de icono Bombilla](media/bulb-cs.png) que aparece.
     * Haga clic en el botón ![de icono Bombilla](media/bulb-cs.png) que aparece en el margen izquierdo si el cursor de texto ya está en la línea con el subrayado ondulado de color rojo.

   ![Vista previa de la implementación de la clase](media/abstract-preview-cs.png)

   >[!TIP]
   >Use el vínculo [**Vista previa de los cambios**](../../ide/preview-changes.md) en la parte inferior de la ventana de vista previa para ver todos los cambios que se aplicarán antes de hacer la selección.
   >
   >Además, puede usar los vínculos **Documento**, **Proyecto** y **Solución** de la parte inferior de la ventana de vista previa para crear las firmas de método adecuadas entre las múltiples clases que heredan de la clase abstracta.

1. Las firmas de método abstracto se crearán automáticamente y estarán listas para su implementación.

   ![Resultado de la implementación de la clase](media/abstract-result-cs.png)

## <a name="see-also"></a>Vea también

[Generación de código](../code-generation-in-visual-studio.md)  
[Vista previa de cambios](../../ide/preview-changes.md)
