---
title: 'Paso 5: Agregar controles al formulario'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: dc2746f4-0b5c-4674-9ef7-f40f94150f52
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a7a0167d4d5af125e706350002ccf8a17e459414
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34748561"
---
# <a name="step-5-add-controls-to-your-form"></a>Paso 5: Agregar controles al formulario
En este paso, se agregan controles, como un control <xref:System.Windows.Forms.PictureBox> y un control <xref:System.Windows.Forms.CheckBox>, al formulario. Luego puede agregar controles <xref:System.Windows.Forms.Button> al formulario.

 ![vínculo al vídeo](../data-tools/media/playvideo.gif)Para obtener una versión en vídeo de este tema, vea el [Tutorial 1: Crear un visor de imágenes en Visual Basic (vídeo 2)](http://go.microsoft.com/fwlink/?LinkId=205211) o el [Tutorial 1: Crear un visor de imágenes en C# (vídeo 2)](http://go.microsoft.com/fwlink/?LinkId=205200). En estos vídeos se utilizó una versión anterior de Visual Studio, por lo que hay ligeras diferencias en algunos comandos de menú y otros elementos de la interfaz de usuario. Sin embargo, los conceptos y procedimientos funcionan de forma similar en la versión actual de Visual Studio.

## <a name="to-add-controls-to-your-form"></a>Para agregar controles al formulario

1.  Vaya a la pestaña **Cuadro de herramientas** (situada a la izquierda del IDE de Visual Studio) y expanda el grupo **Controles comunes**. Se muestran los controles más comunes que suelen aparecer en los formularios.

2.  Elija el control **TableLayoutPanel** del formulario. Para comprobar que TableLayoutPanel está activado, asegúrese de que su nombre aparezca en el cuadro de lista desplegable situado en la parte superior de la ventana **Propiedades**. También puede elegir controles de formulario mediante el cuadro de lista desplegable que se encuentra en la parte superior de la ventana **Propiedades**. Suele resultar más fácil hacerlo de esta manera que elegir un control minúsculo con el mouse.

3.  Haga doble clic en el elemento **PictureBox** para agregar un control PictureBox al formulario. Dado que TableLayoutPanel está acoplado de forma que ocupa el formulario, el IDE agrega el control PictureBox en la primera celda vacía (la esquina superior izquierda).

4.  Elija el nuevo control **PictureBox** para seleccionarlo y, a continuación, elija el triángulo negro de este control para mostrar la lista de tareas, tal y como se muestra en la imagen siguiente.

     ![Tareas de PictureBox](../ide/media/express_pictureboxtasks.png)
**PictureBox** tasks

    > [!NOTE]
    >  Si agrega accidentalmente un tipo equivocado de control a TableLayoutPanel, puede eliminarlo. Haga clic con el botón derecho en el control y, después, pulse **Eliminar** en el menú contextual. También puede quitar controles del formulario mediante la barra de menús. En la barra de menús, pulse **Editar** > **Deshacer** o **Editar** > **Eliminar**.

5.  Pulse el vínculo **Acoplar en contenedor primario**. Se establece automáticamente la propiedad **Dock** de PictureBox en **Fill**. Para verlo, seleccione el control **PictureBox**, vaya a la ventana **Propiedades** y asegúrese de que la propiedad **Dock** está establecida en **Fill**.

6.  Haga que PictureBox abarque ambas columnas cambiando su propiedad **ColumnSpan**. Pulse el control **PictureBox** y establezca su propiedad **ColumnSpan** en **2**. Además, cuando el PictureBox está vacío, se debe mostrar un marco vacío. Establezca su propiedad **BorderStyle** en **Fixed3D**.

    > [!NOTE]
    >  Si no se muestra ninguna propiedad **ColumnSpan** en el control PictureBox, es probable que se haya agregado PictureBox al formulario en lugar de TableLayoutPanel. Para corregir esto, elija el control **PictureBox**, elimínelo, elija el control **TableLayoutPanel** y, a continuación, agregue un nuevo control PictureBox.

7.  Seleccione el control **TableLayoutPanel** del formulario y, después, agregue un control CheckBox al formulario. Haga doble clic en el elemento **CheckBox** del **cuadro de herramientas** para agregar un nuevo control CheckBox a la siguiente celda libre de la tabla. Como el control PictureBox ocupa las dos primeras celdas del control TableLayoutPanel, el control CheckBox se agrega en la celda inferior izquierda. Seleccione la propiedad **Text** y escriba la palabra **Stretch**, como se muestra en la imagen siguiente.

     ![Control TextBox con la propiedad Stretch](../ide/media/express_pictureviewercheckbox.png)
**TextBox** control with **Stretch** pr

8.  Seleccione el control **TableLayoutPanel** del formulario, vaya al grupo **Contenedores** del **cuadro de herramientas** (donde ha obtenido el control TableLayoutPanel) y haga doble clic en el elemento **FlowLayoutPanel** para agregar un nuevo control a la última celda de PictureBox (en la parte inferior derecha). Después, acople el control FlowLayoutPanel en TableLayoutPanel (para ello, pulse **Acoplar en contenedor primario** en la lista de tareas del triángulo negro de FlowLayoutPanel o establezca la propiedad **Dock** de FlowLayoutPanel en **Fill**).

    > [!NOTE]
    >  Un <xref:System.Windows.Forms.FlowLayoutPanel> es un contenedor que organiza otros controles en filas ordenadas. Al cambiar el tamaño de FlowLayoutPanel, coloca todos los controles que contiene en una sola fila, siempre que tenga espacio para ello. De lo contrario, los organiza en líneas, uno encima de otro. Vamos a utilizar un control FlowLayoutPanel para contener cuatro botones. Si al agregar los botones se organizan uno encima de otro, asegúrese de que el control FlowLayoutPanel está seleccionado antes de agregarlos. Aunque hemos dicho anteriormente que cada celda puede contener un solo control, la celda inferior derecha del control TableLayoutPanel tiene cuatro controles de botón. Esto es porque se puede colocar un control en una celda que contiene otros controles. Este tipo de control se denomina contenedor y FlowLayoutPanel es un contenedor.

## <a name="to-add-buttons"></a>Para agregar botones

1.  Elija el nuevo control FlowLayoutPanel que acaba de agregar. Vaya a **Controles comunes** en el **cuadro de herramientas** y haga doble clic en el elemento **Button** para agregar un control de botón denominado **button1** al control FlowLayoutPanel. Repita el proceso para agregar otro botón. El IDE determina que ya hay un botón denominado **button1**, de modo que denomina **button2** al siguiente.

2.  Normalmente, se agregan los demás botones mediante el **Cuadro de herramientas**. Esta vez, pulse **button2** y, después, en la barra de menús, pulse **Edición** > **Copiar** (o presione **Ctrl**+**C**). En la barra de menús, pulse **Edición** > **Pegar** (o presione **Ctrl**+**V**) para pegar una copia del botón. Vuelva a pegarlo otra vez. Ahora el IDE ha agregado **button3** y **button4** al control FlowLayoutPanel.

    > [!NOTE]
    >  Puede copiar y pegar cualquier control. El IDE da nombre y coloca los nuevos controles de una manera lógica. Si se pega un control en un contenedor, el IDE elige el siguiente espacio lógico para colocarlo.

3.  Pulse el primer botón y establezca su propiedad **Text** en **Mostrar una imagen**. Después establezca las propiedades **Text** de los otros tres botones siguientes en **Borrar la imagen**, **Establecer el color de fondo** y **Cerrar**.

4.  El paso siguiente consiste en cambiar el tamaño de los botones y organizarlos de modo que estén alineados a la derecha del panel. Pulse el control **FlowLayoutPanel** y fíjese en su propiedad **FlowDirection**. Cámbiela de modo que quede establecida en **RightToLeft**. En cuanto lo haga, los botones deberían alinearse a la derecha de la celda, en orden inverso de modo que el botón **Mostrar una imagen** quede a la derecha.

    > [!NOTE]
    >  Si los botones siguen en orden incorrecto, puede arrastrarlos alrededor de FlowLayoutPanel para reorganizarlos en cualquier orden. Puede elegir un botón y arrastrarlo a la izquierda o a la derecha.

5.  Pulse el botón **Cerrar** para seleccionarlo. Mantenga presionada la tecla **CTRL** y elija los otros tres botones para que todos estén seleccionados. Mientras todos los botones están seleccionados, vaya a la ventana **Propiedades** y desplácese hacia arriba hasta la propiedad **AutoSize**. Esta propiedad indica al botón que cambie el tamaño automáticamente para ajustarse al texto que contiene. Establézcala en **true**. Ahora, los botones deberían tener el tamaño y orden correctos. (Si los cuatro botones están seleccionados, puede cambiar las cuatro propiedades **AutoSize** al mismo tiempo). En la siguiente imagen se muestran los cuatro botones.

     ![Visor de imágenes con cuatro botones](../ide/media/express_autosize.png)
**Picture Viewer** with four buttons

6.  Ahora, ejecute de nuevo el programa para ver el formulario que acaba de diseñar. Al elegir los botones y la casilla todavía no sucede nada, pero funcionarán pronto.

## <a name="to-continue-or-review"></a>Para continuar o revisar

-   Para ir al siguiente paso del tutorial, vea [Paso 6: Asignar un nombre a los controles de botón](../ide/step-6-name-your-button-controls.md).

-   Para volver al paso anterior del tutorial, vea [Paso 4: Diseñar un formulario con un control TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md).
