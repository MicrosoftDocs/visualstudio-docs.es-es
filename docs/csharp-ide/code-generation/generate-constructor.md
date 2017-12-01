---
title: "Generar un constructor - generación de código (C#) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2280cfa-a9ec-4b56-9d94-c8fd384db980
author: kuhlenh
ms.author: kaseyu
manager: ghogen
ms.openlocfilehash: 668036b5a9c963a48255e8425c0d443fce4b8bb7
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/29/2017
---
# <a name="generate-a-constructor-in-c"></a>Generar un constructor en C# #
**¿Qué:** le permite generar inmediatamente el código para un nuevo constructor en una clase. 

**Cuándo:** introduce un nuevo constructor y desea correctamente declarar automáticamente o modificar un constructor existente. 

**Por este motivo:** podría declarar el constructor antes de usarlo, sin embargo, esta característica generará, con los parámetros adecuados, automáticamente. Además, la modificación de un constructor existente requiere actualizar todos los sitios de llamada a menos que utilice esta característica se actualizan automáticamente.

**Cómo:** para generar un constructor de varias maneras:
- [Generar constructor y elegir miembros](#pick)
- [Generar el constructor de los campos seleccionados](#selection)
- [Generar el constructor de uso nueva](#usage)
- [Agregue el parámetro al constructor existente](#addparameter)
- [Crear e inicializar el campo o la propiedad de un parámetro de constructor](#create)

## <a id = "pick"></a>Generar constructor y elegir miembros
1. Coloque el cursor en cualquier línea vacía en una clase:

   ![Cursor en una línea vacía](media/constructor1_highlight.png)

1. A continuación, realice una de las siguientes acciones:
   * **Teclado**
     * Presione **Ctrl +.** Para activar el **acciones rápidas y refactorizaciones** menú y seleccione **generar constructor...**  desde la ventana emergente de ventana de vista previa.
   * **Mouse**
     * Haga clic en y seleccione el **acciones rápidas y refactorizaciones** menú y seleccione **generar constructor...**  desde la ventana emergente de ventana de vista previa.
     * Haga clic en el botón ![Bombilla](media/bulb.png) icono que aparece en el margen izquierdo si el cursor de texto ya está en la línea vacía de la clase.

   ![Generar vista previa de constructor](media/constructor1_preview.png)

1. Aparecerá un cuadro de diálogo lo que le permite elegir qué miembros que desea que se pueden usar como parámetros de constructor, así como ordénelas (con arriba y abajo). Presione **Aceptar** para confirmar los cambios.
  
   ![Cuadro de diálogo de selección miembros](media/constructor1_dialog.png)

   >[!TIP] 
   >Puede comprobar la **que agregar comprobaciones null** casilla de verificación para generar automáticamente las comprobaciones de null para los parámetros de constructor.

1. El constructor se creará con los parámetros seleccionados en el orden especificado.
   ![Generar el resultado del constructor](media/constructor1_result.png)

## <a id="selection"></a>Generar el constructor de los campos seleccionados
1. Resaltar los miembros que se va a tener en su constructor generado: ![resaltar los miembros](media/constructor2_highlight.png)

1. A continuación, realice una de las siguientes acciones:
   * **Teclado**
     * Presione **Ctrl +.** Para activar el **acciones rápidas y refactorizaciones** menú y seleccione **generar constructor 'TypeName(...)'**  desde la ventana emergente de ventana de vista previa.
   * **Mouse**
     * Haga clic en y seleccione el **acciones rápidas y refactorizaciones** menú y seleccione **generar constructor 'TypeName(...)'**  desde la ventana emergente de ventana de vista previa.
     * Haga clic en el botón ![Bombilla](media/bulb.png) icono que aparece en el margen izquierdo si el cursor de texto ya está en la línea con la selección.

     ![Generar vista previa de Constructor](media/constructor2_preview.png)

1. El constructor se creará con los parámetros seleccionados.
     ![Generar el resultado del Constructor](media/constructor2_result.png)

## <a id="usage"></a>Generar el constructor de uso nueva
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

## <a id="selection"></a>Agregue el parámetro al constructor existente
1. Agregar un parámetro a una instancia de objeto existente.

1. Coloque el cursor en la línea donde hay un subrayado ondulado de color rojo que indica que ha utilizado un constructor que aún no existe.
    
    ![Generar constructor resaltado](media/constructor4_highlight.png)

1. A continuación, realice una de las siguientes acciones:
   * **Teclado**
     * Presione **Ctrl +.** Para activar el **acciones rápidas y refactorizaciones** menú y seleccione **agregar parámetros a 'TypeName(...)'**  desde la ventana emergente de ventana de vista previa.
   * **Mouse**
     * Haga clic en y seleccione el **acciones rápidas y refactorizaciones** menú y seleccione **agregar parámetros a 'TypeName(...)'**  desde la ventana emergente de ventana de vista previa.
     * Mantenga el mouse sobre el subrayado ondulado de color rojo y haga clic en el ![Bombilla](media/bulb.png) icono que aparece.
     * Haga clic en el botón ![Bombilla](media/bulb.png) icono que aparece en el margen izquierdo si el cursor de texto ya está en la línea con la línea roja ondulada.

    ![Generar vista previa de constructor](media/constructor4_preview.png)

1. El parámetro se agregará automáticamente con su tipo inferido a partir de su uso.
   
   ![Generar el resultado del constructor](media/constructor4_result.png)

## <a id="create"></a>Crear e inicializar el campo o la propiedad de un parámetro de constructor
1. Desde un constructor existente, agregue un parámetro:

   ![Generar constructor resaltado](media/constructor5_highlight.png)

1. Coloque el cursor dentro del parámetro recién agregado.

1. A continuación, realice una de las siguientes acciones:
   * **Teclado**
     * Presione **Ctrl +.** Para activar el **acciones rápidas y refactorizaciones** menú y seleccione **crear e inicializar la propiedad 'YourProperty'** o **crear e inicializar campo 'YourField'** desde el Menú emergente de ventana de vista previa.
   * **Mouse**
     * Haga clic en y seleccione el **acciones rápidas y refactorizaciones** menú y seleccione **crear e inicializar la propiedad 'YourProperty'** o **crear e inicializar campo 'YourField'**desde la ventana emergente de ventana de vista previa.
     * Haga clic en el botón ![Bombilla](media/bulb.png) icono que aparece en el margen izquierdo si el cursor de texto ya está en la línea con el parámetro agregado.

   ![Generar vista previa de constructor](media/constructor5_preview.png)

1. Se creará y se denomina automáticamente para que coincida con los tipos de la propiedad de campo.

   ![Generar el resultado del constructor](media/constructor5_result.png)
  
## <a name="see-also"></a>Vea también  
[Code Generation (C#)](../code-generation-csharp.md) (Generación de código (C#))  
[Vista previa de cambios](../../ide/preview-changes.md)