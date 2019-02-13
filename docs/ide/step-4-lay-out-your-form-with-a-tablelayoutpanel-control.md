---
title: 'Paso 4: Diseñar un formulario con un control TableLayoutPanel'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 61acde79-e115-4bad-bb06-1fbe37717a3e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7083a8874b699716d834ea69ba88c30225acec88
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55926117"
---
# <a name="step-4-lay-out-your-form-with-a-tablelayoutpanel-control"></a>Paso 4: Diseñar un formulario con un control TableLayoutPanel
En este paso, agregará un control <xref:System.Windows.Forms.TableLayoutPanel> al formulario. El control TableLayoutPanel ayuda a alinear correctamente los controles del formulario que se agregarán posteriormente.

 ![vínculo al vídeo](../data-tools/media/playvideo.gif)Para obtener una versión en vídeo de este tema, vea [Tutorial 1: Crear un visor de imágenes en Visual Basic - Vídeo 2](http://go.microsoft.com/fwlink/?LinkId=205211) o [Tutorial 1: Crear un visor de imágenes en C# - Vídeo 2](http://go.microsoft.com/fwlink/?LinkId=205200). En estos vídeos se utilizó una versión anterior de Visual Studio, por lo que hay ligeras diferencias en algunos comandos de menú y otros elementos de la interfaz de usuario. Sin embargo, los conceptos y procedimientos funcionan de forma similar en la versión actual de Visual Studio.

## <a name="to-lay-out-your-form-with-a-tablelayoutpanel-control"></a>Para diseñar el formulario con un control TableLayoutPanel

1.  En el lado izquierdo del IDE de Visual Studio, busque la pestaña **Cuadro de herramientas**. Pulse la pestaña **Cuadro de herramientas** y aparecerá el **cuadro de herramientas**. (O bien, en la barra de menús, pulse **Ver** > **Cuadro de herramientas**).

2.  Pulse el símbolo del triángulo pequeño que se encuentra junto al grupo **Contenedores** para abrirlo, tal y como se muestra en la siguiente imagen.

     ![Grupo de contenedores](../ide/media/express_toolbox.png)
**Containers** group

3.  Puede agregar controles como botones, casillas y etiquetas al formulario. Haga doble clic en el control TableLayoutPanel del **cuadro de herramientas**. (También puede arrastrar el control desde el Cuadro de herramientas hasta el formulario). Al hacerlo, el IDE agrega un control TableLayoutPanel al formulario, como se muestra en la siguiente imagen.

     ![TableLayoutPanel (control)](../ide/media/express_formtablelayout.png)
**TableLayoutPanel** control

    > [!NOTE]
    >  Si, después de agregar el control TableLayoutPanel, aparece una ventana dentro del formulario con el título **Tareas de TableLayoutPanel**, haga clic en cualquier parte del formulario para cerrarla. Aprenderemos más cosas sobre esta ventana más adelante en el tutorial.

     Observe que el **cuadro de herramientas** se expande para abarcar el formulario cuando se elige su pestaña, y se cierra cuando se hace clic fuera de él. Se trata de la característica Ocultar automáticamente del IDE. Puede activarlo o desactivarlo en cualquiera de las ventanas eligiendo el marcador de la esquina superior derecha de la ventana para hacer que se oculte automáticamente y que quede bloqueado en su lugar. El icono del pin tiene este aspecto.

     ![Icono de pin](../ide/media/express_pushpintoolbox.png)
**Pushpin** icon

4.  Pulse TableLayoutPanel para asegurarse de que está seleccionado. Puede comprobar qué control está seleccionado examinando la lista desplegable de la parte superior de la ventana **Propiedades**, como se muestra en la siguiente imagen.

     ![Ventana Propiedades en la que se muestra el control TableLayoutPanel](../ide/media/express_controlspropwin.png)
**Properties** window showing **TableLayoutPanel** control

5.  Pulse el botón **Alfabético** en la barra de herramientas de la ventana **Propiedades**. Esto hace que la lista de propiedades de la ventana **Propiedades** aparezca en orden alfabético, lo que facilitará la localización de propiedades en este tutorial.

6.  El selector de controles es una lista desplegable que figura en la parte superior de la ventana **Propiedades**. En este ejemplo, muestra que un control denominado `tableLayoutPanel1` está seleccionado. Puede seleccionar los controles eligiendo un área en el **Diseñador de Windows Forms** o eligiéndolos en el selector de controles. Ahora que TableLayoutPanel está seleccionado, busque la propiedad **Dock** y elija **Dock**, que debería estar establecida en **None**. Observe que aparece una flecha de lista desplegable al lado del valor. Pulse la flecha y, después, seleccione el botón **Rellenar** (el botón grande del centro), tal y como se muestra en la siguiente imagen.

     ![Ventana Propiedades con la opción Rellenar seleccionada](../ide/media/express_docktable.png)
**Properties** window with **Fill** selected

     *Acoplar* en Visual Studio hace referencia a cuando una ventana está asociada a otra ventana o área en el IDE. Por ejemplo, la ventana **Propiedades** puede estar desacoplada, es decir, estar desasociada y flotar libremente en Visual Studio, o puede estar acoplada en el **Explorador de soluciones**.

7.  Después de establecer la propiedad **Dock** de TableLayoutPanel en **Fill**, el panel rellena el formulario completo. Si vuelve a cambiar el tamaño del formulario, TableLayoutPanel permanecerá acoplado y cambiará de tamaño para ajustarse al formulario.

    > [!NOTE]
    >  TableLayoutPanel funciona como una tabla de Microsoft Office Word: Tiene filas y columnas y una celda individual puede abarcar varias filas y columnas. Cada celda puede contener un control (como un botón, una casilla o una etiqueta). Este control TableLayoutPanel va a contener un control <xref:System.Windows.Forms.PictureBox> que abarcará completamente su fila superior, un control <xref:System.Windows.Forms.CheckBox> en la celda inferior izquierda, y cuatro controles <xref:System.Windows.Forms.Button> en la celda inferior derecha.

8.  Actualmente, TableLayoutPanel tiene dos filas del mismo tamaño y dos columnas del mismo tamaño. Tenemos que cambiar su tamaño de modo que la fila superior y la columna derecha sean mucho mayores. En el **Diseñador de Windows Forms**, seleccione TableLayoutPanel. En la esquina superior derecha, hay un botoncito triangular de color negro, con el siguiente aspecto.

     ![Botón Triángulo](../ide/media/express_iconblacktriangle.gif)
**Triangle** button

     Este botón indica que el control tiene tareas que le ayudan a establecer sus propiedades automáticamente.

9. Elija el triángulo para mostrar la lista de tareas del control, tal y como se muestra en la siguiente imagen.

     ![Tareas de TableLayoutPanel](../ide/media/express_tablepanel.png)
**TableLayoutPanel** tasks

10. Pulse la tarea **Editar filas y columnas** para abrir la ventana **Estilos de columna y fila**. Elija **Column1** y establezca su tamaño en el 15 por ciento; para ello, asegúrese de que el botón **Porcentaje** está seleccionado y escriba **15** en el cuadro **Porcentaje**. (Se trata de un control <xref:System.Windows.Forms.NumericUpDown>, que usará en un tutorial posterior). Pulse **Column2** y establézcala en el 85 por ciento. No pulse todavía el botón **Aceptar**, ya que se cerraría la ventana. (Si lo hace, puede volver a abrirla mediante la lista de tareas.)

     ![Estilos de columna y fila de TableLayoutPanel](../ide/media/vs_tablelayoutpanel_setup.png)
**TableLayoutPanel** column and row styles

11. En la lista desplegable **Mostrar** de la parte superior de la ventana, pulse **Filas**. Establezca **Row1** en el 90 por ciento y **Row2** en el 10 por ciento.

12. Elija el botón **Aceptar** . TableLayoutPanel debería tener ahora una fila superior grande, una fila inferior pequeña, una columna izquierda pequeña y una columna derecha grande. Puede cambiar el tamaño de las filas y columnas de TableLayoutPanel eligiendo **tableLayoutPanel1** en el formulario y arrastrando sus bordes de fila y columna.

     ![Form1 con TableLayoutPanel cambiado de tamaño](../ide/media/vs_formafterlayoutpanel.png)
**Form1** with resized **TableLayoutPanel**

## <a name="to-continue-or-review"></a>Para continuar o revisar

-   Para ir al siguiente paso del tutorial, vea [Paso 5: Agregar controles al formulario](../ide/step-5-add-controls-to-your-form.md).

-   Para volver al paso anterior del tutorial, vea [Paso 3: Establecer las propiedades del formulario](../ide/step-3-set-your-form-properties.md).
