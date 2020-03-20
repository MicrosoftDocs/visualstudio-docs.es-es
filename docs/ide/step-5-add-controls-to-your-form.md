---
title: 'Paso 5: Agregar controles al formulario'
ms.date: 08/30/2019
ms.assetid: dc2746f4-0b5c-4674-9ef7-f40f94150f52
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 631def96fc7e4b5d7858ea3474492b41c526da65
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579353"
---
# <a name="step-5-add-controls-to-your-form"></a>Paso 5: Agregar controles al formulario

En este paso, se agregan controles, como un control <xref:System.Windows.Forms.PictureBox> y un control <xref:System.Windows.Forms.CheckBox>, al formulario. Luego puede agregar controles <xref:System.Windows.Forms.Button> al formulario.

## <a name="how-to-add-controls-to-your-form"></a>Procedimientos para agregar controles al formulario

1. Seleccione la pestaña **Cuadro de herramientas** en el lado izquierdo del IDE de Visual Studio (o presione **Ctrl**+**Alt**+**X**) y, después, expanda el grupo **Controles comunes**. Se muestran los controles más comunes que suelen aparecer en los formularios.

1. Haga doble clic en el elemento **PictureBox** para agregar un control PictureBox al formulario. Dado que TableLayoutPanel está acoplado de forma que ocupa el formulario, el IDE agrega el control PictureBox en la primera celda vacía (la esquina superior izquierda).

1. Elija el nuevo control **PictureBox** para seleccionarlo y, después, elija el triángulo negro de este control para mostrar la lista de tareas, como se muestra en la captura de pantalla siguiente.

    ![Tareas de PictureBox](../ide/media/express_pictureboxtasks.png)<br/>*Tareas de* ****PictureBox****

    > [!NOTE]
    > Si agrega accidentalmente un tipo equivocado de control a TableLayoutPanel, puede eliminarlo. Haga clic con el botón derecho en el control y, después, pulse **Eliminar** en el menú contextual. También puede quitar controles del formulario mediante la barra de menús. En la barra de menús, pulse **Editar** > **Deshacer** o **Editar** > **Eliminar**.

1. En el menú **Tareas de PictureBox** del control **PictureBox**, seleccione el vínculo **Acoplar en contenedor primario**. Se establece automáticamente la propiedad **Dock** de PictureBox en **Fill**. Para verlo, seleccione el control **PictureBox**, vaya a la ventana **Propiedades** y asegúrese de que la propiedad **Dock** está establecida en **Fill**.

1. Haga que PictureBox abarque ambas columnas cambiando su propiedad **ColumnSpan**. En **PictureBox**, seleccione el control **PictureBox** y establezca su propiedad **ColumnSpan** en **2**. Además, cuando el PictureBox está vacío, se debe mostrar un marco vacío. Establezca su propiedad **BorderStyle** en **Fixed3D**.

    > [!NOTE]
    > Si no se muestra ninguna propiedad **ColumnSpan** en el control PictureBox, es probable que se haya agregado PictureBox al formulario en lugar de TableLayoutPanel. Para corregir esto, elija el control **PictureBox**, elimínelo, elija el control **TableLayoutPanel** y, a continuación, agregue un nuevo control PictureBox.

1. Seleccione el control **TableLayoutPanel** del formulario y, después, agregue un control CheckBox al formulario. Haga doble clic en el elemento **CheckBox** del **cuadro de herramientas** para agregar un nuevo control CheckBox a la siguiente celda libre de la tabla. Como el control PictureBox ocupa las dos primeras celdas del control TableLayoutPanel, el control CheckBox se agrega en la celda inferior izquierda. Seleccione la propiedad **Text** y escriba la palabra **Stretch**, como se muestra en la imagen siguiente.

    ![Control TextBox con la propiedad Stretch](../ide/media/express_pictureviewercheckbox.png)<br/>***Control*** TextBox*con la* ***propiedad*** *Stretch*

1. Seleccione el control **TableLayoutPanel** del formulario, vaya al grupo **Contenedores** del **Cuadro de herramientas** (donde ha obtenido el control TableLayoutPanel) y haga doble clic en el elemento **FlowLayoutPanel** para agregar un nuevo control a la última celda (en la parte inferior derecha). Después, acople el control FlowLayoutPanel en TableLayoutPanel. Para ello, seleccione **Acoplar en contenedor primario** en la lista de tareas del triángulo negro de FlowLayoutPanel, o bien establezca la propiedad **Dock** de FlowLayoutPanel en **Relleno**.

    > [!NOTE]
    > Un elemento <xref:System.Windows.Forms.FlowLayoutPanel> es un contenedor que organiza otros controles en una fila, una detrás de otra. Al cambiar el tamaño de FlowLayoutPanel, coloca todos sus controles en una sola fila, si tiene espacio para ello. De lo contrario, los organiza en líneas, uno encima de otro. <br/><br/>Aquí usará un control FlowLayoutPanel para contener cuatro botones. Si los botones se organizan uno encima de otro al agregarlos, asegúrese de que selecciona el control FlowLayoutPanel antes de agregarlos. <br/><br/>(Normalmente, cada celda solo contiene un control. En este ejemplo, la celda inferior derecha de TableLayoutPanel contiene cuatro controles de botón. ¿Por qué?  Porque FlowLayoutPanel es un control contenedor, que es un control en una celda que contiene otros controles).

## <a name="to-add-buttons"></a>Para agregar botones

1. Elija el nuevo control FlowLayoutPanel que acaba de agregar. Vaya a **Controles comunes** en el **cuadro de herramientas** y haga doble clic en el elemento **Button** para agregar un control de botón denominado **button1** al control FlowLayoutPanel. Repita el proceso para agregar otro botón. El IDE determina que ya hay un botón denominado **button1**, de modo que denomina **button2** al siguiente.

1. Normalmente, los demás botones se agregan mediante el **Cuadro de herramientas**. Esta vez, seleccione **button2** y, después, en la barra de menús, seleccione **Edición** > **Copiar** (o presione **Ctrl**+**C**). Después, seleccione **Edición** > **Pegar** en la barra de menús, (o presione **Ctrl**+**V**) para pegar una copia del botón. Vuelva a pegarlo otra vez. Observe que en el IDE se agregan **button3** y **button4** al control FlowLayoutPanel.

    > [!NOTE]
    > Puede copiar y pegar cualquier control. El IDE da nombre y coloca los nuevos controles de una manera lógica. Si se pega un control en un contenedor, el IDE elige el siguiente espacio lógico para colocarlo.

1. Pulse el primer botón y establezca su propiedad **Text** en **Mostrar una imagen**. Después establezca las propiedades **Text** de los otros tres botones siguientes en **Borrar la imagen**, **Establecer el color de fondo** y **Cerrar**.

1. A continuación, se cambiará el tamaño de los botones y se organizarán para alinearlos a la derecha del panel. Pulse el control **FlowLayoutPanel** y fíjese en su propiedad **FlowDirection**. Cámbiela de modo que quede establecida en **RightToLeft**.

   Los botones deberían alinearse a la derecha de la celda, en orden inverso de modo que el botón **Mostrar una imagen** quede a la derecha.

    > [!NOTE]
    > Si los botones siguen en orden incorrecto, puede arrastrarlos alrededor de FlowLayoutPanel para reorganizarlos en cualquier orden. Puede elegir un botón y arrastrarlo a la izquierda o a la derecha.

1. Pulse el botón **Cerrar** para seleccionarlo. Después, para elegir el resto de los botones al mismo tiempo, mantenga presionada la tecla **Ctrl** y selecciónelos.

   Después de seleccionar todos los botones, vaya a la ventana **Propiedades** y desplácese hacia arriba hasta la propiedad **AutoSize**. Esta propiedad indica al botón que cambie el tamaño automáticamente para ajustarse al texto que contiene. Establézcala en **True**.

   Ahora, los botones deberían tener el tamaño y orden correctos. (Si los cuatro botones están seleccionados, puede cambiar las cuatro propiedades **AutoSize** al mismo tiempo). En la imagen siguiente se muestran los cuatro botones.

    ![Visor de imágenes con cuatro botones](../ide/media/express_autosize.png)<br/>***Visor de imágenes*** *con cuatro botones*

1. Ahora vuelva a ejecutar el programa para ver los cambios.

   Observe que los botones y la casilla no hacen nada todavía, pero pronto lo harán.

## <a name="to-continue-or-review"></a>Para continuar o revisar

* Para ir al siguiente paso del tutorial, consulte **[Paso 6: Asignar un nombre a los controles de botón](../ide/step-6-name-your-button-controls.md)** .

* Para volver al paso anterior del tutorial, vea [Paso 4: Diseñar un formulario con un control TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md).

## <a name="see-also"></a>Vea también

* [Tutorial 2: Creación de una prueba matemática cronometrada](tutorial-2-create-a-timed-math-quiz.md)
* [Tutorial 3: Creación de un juego de formar parejas](tutorial-3-create-a-matching-game.md)
