---
title: 'Paso 4: Diseñar un formulario con un control TableLayoutPanel | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 61acde79-e115-4bad-bb06-1fbe37717a3e
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f61a308fcd68b03852176087438c22c245078693
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851549"
---
# <a name="step-4-lay-out-your-form-with-a-tablelayoutpanel-control"></a>Paso 4: Diseñar un formulario con un control TableLayoutPanel
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este paso, agregará un control `TableLayoutPanel` al formulario. El control TableLayoutPanel ayuda a alinear correctamente los controles del formulario que se agregarán posteriormente.

 ![vínculo a vídeo](../data-tools/media/playvideo.gif "PlayVideo") Para obtener una versión en vídeo de este tema, vea el [tutorial 1: crear un visor de imágenes en Visual Basic-vídeo 2 o el](https://msdn.microsoft.com/vbasic/gg315945.aspx) [tutorial 1: crear un visor de imágenes en C# (vídeo 2)](https://msdn.microsoft.com/vcsharp/gg278410.aspx). En estos vídeos se utilizó una versión anterior de Visual Studio, por lo que hay ligeras diferencias en algunos comandos de menú y otros elementos de la interfaz de usuario. Sin embargo, los conceptos y procedimientos funcionan de forma similar en la versión actual de Visual Studio.

### <a name="to-lay-out-your-form-with-a-tablelayoutpanel-control"></a>Para diseñar el formulario con un control TableLayoutPanel

1. En el lado izquierdo del IDE de Visual Studio, busque la pestaña **cuadro de herramientas** . Elija la pestaña **cuadro de herramientas** y aparecerá el cuadro de herramientas. (O bien, en la barra de menús, pulse **Ver**, **Cuadro de herramientas**).

2. Pulse el símbolo del triángulo pequeño que se encuentra junto al grupo **Contenedores** para abrirlo, tal y como se muestra en la siguiente imagen.

     ![Grupo de contenedores](../ide/media/express-toolbox.png "Express_Toolbox") Grupo de contenedores

3. Puede agregar controles como botones, casillas y etiquetas al formulario. Haga doble clic en el control `TableLayoutPanel` en el cuadro de herramientas. (O bien, puede arrastrar el control desde el cuadro de herramientas hasta el formulario). Al hacerlo, el IDE agrega un `TableLayoutPanel` control al formulario, como se muestra en la siguiente imagen.

     ![Control TableLayoutPanel](../ide/media/express-formtablelayout.png "Express_FormTableLayout") Control TableLayoutPanel

    > [!NOTE]
    > Si, después de agregar el control TableLayoutPanel, aparece una ventana dentro del formulario con el título **Tareas de TableLayoutPanel**, haga clic en cualquier parte del formulario para cerrarla. Aprenderemos más cosas sobre esta ventana más adelante en el tutorial.

     Observe que el Cuadro de herramientas se expande para abarcar el formulario cuando se elige su pestaña, y se cierra cuando se hace clic fuera de él. Se trata de la característica Ocultar automáticamente del IDE. Puede activarlo o desactivarlo en cualquiera de las ventanas eligiendo el marcador de la esquina superior derecha de la ventana para hacer que se oculte automáticamente y que quede bloqueado en su lugar. El icono del pin tiene este aspecto.

     ![Icono de PIN](../ide/media/express-pushpintoolbox.png "Express_PushpinToolbox") Icono de PIN

4. Pulse **TableLayoutPanel** para asegurarse de que está seleccionado. Puede comprobar qué control está seleccionado examinando la lista desplegable de la parte superior de la ventana **Propiedades**, como se muestra en la siguiente imagen.

     ![Ventana Propiedades que muestra el control TableLayoutPanel](../ide/media/express-controlspropwin.png "Express_ControlsPropWin") ventana Propiedades que muestra el control TableLayoutPanel

5. Pulse el botón **Alfabético** en la barra de herramientas de la ventana **Propiedades**. Esto hace que la lista de propiedades de la ventana **Propiedades** aparezca en orden alfabético, lo que facilitará la localización de propiedades en este tutorial.

6. El selector de controles es una lista desplegable que figura en la parte superior de la ventana **Propiedades**. En este ejemplo, muestra que un control denominado `tableLayoutPanel1` está seleccionado. Puede seleccionar los controles eligiendo un área en el Diseñador de Windows Forms o eligiéndolos en el selector de controles. Ahora que `TableLayoutPanel` está seleccionado, busque la propiedad **Dock** y pulse **Dock**, que debería estar establecida en **None**. Observe que aparece una flecha de lista desplegable al lado del valor. Pulse la flecha y, después, seleccione el botón **Rellenar** (el botón grande del centro), tal y como se muestra en la siguiente imagen.

     ![Ventana Propiedades con relleno seleccionado](../ide/media/express-docktable.png "Express_DockTable") ventana Propiedades con relleno seleccionado

     *Acoplar* en Visual Studio hace referencia a cuando una ventana está asociada a otra ventana o área en el IDE. Por ejemplo, la ventana Propiedades puede estar desacoplada, es decir, estar desasociada y flotar libremente en Visual Studio, o puede estar acoplada en el **Explorador de soluciones**.

7. Después de establecer la propiedad **Dock** de TableLayoutPanel en **Fill**, el panel rellena el formulario completo. Si vuelve a cambiar el tamaño del formulario, TableLayoutPanel permanecerá acoplado y cambiará de tamaño para ajustarse al formulario.

    > [!NOTE]
    > TableLayoutPanel funciona exactamente igual que una tabla de Microsoft Office Word: tiene filas y columnas, y una celda individual puede abarcar varias filas y columnas. Cada celda puede contener un control (como un botón, una casilla o una etiqueta). Este control TableLayoutPanel va a contener un control `PictureBox` que abarcará completamente su fila superior, un control `CheckBox` en la celda inferior izquierda, y cuatro controles `Button` en la celda inferior derecha.

8. Actualmente, TableLayoutPanel tiene dos filas del mismo tamaño y dos columnas del mismo tamaño. Tenemos que cambiar su tamaño de modo que la fila superior y la columna derecha sean mucho mayores. En el Diseñador de Windows Forms, seleccione TableLayoutPanel. En la esquina superior derecha, hay un botoncito triangular de color negro, con el siguiente aspecto.

     ![Botón de triángulo](../ide/media/express-iconblacktriangle.gif "Express_IconBlackTriangle") Botón de triángulo

     Este botón indica que el control tiene tareas que le ayudan a establecer sus propiedades automáticamente.

9. Elija el triángulo para mostrar la lista de tareas del control, tal y como se muestra en la siguiente imagen.

     ![Tareas de TableLayoutPanel](../ide/media/express-tablepanel.png "Express_TablePanel") Tareas de TableLayoutPanel

10. Pulse la tarea **Editar filas y columnas** para abrir la ventana **Estilos de columna y fila**. Pulse **Column1** y establezca su tamaño en el 15 por ciento; para ello, asegúrese de que el botón **Porcentaje** está seleccionado y escriba `15` en el cuadro **Porcentaje**. (Este es un `NumericUpDown` control, que se utilizará en un tutorial posterior). Elija **columna2** y establézcalo en 85 por ciento. No pulse todavía el botón **Aceptar**, ya que se cerraría la ventana. (Si lo hace, puede volver a abrirla mediante la lista de tareas.)

     ![Estilos de columna y fila de TableLayoutPanel](../ide/media/vs-tablelayoutpanel-setup.png "VS_TableLayoutPanel_Setup") Estilos de columna y fila de TableLayoutPanel

11. En la lista desplegable **Mostrar** de la parte superior de la ventana, pulse **Filas**. Establezca **Row1** en el 90 por ciento y **Row2** en el 10 por ciento.

12. Elija el botón **Aceptar** . TableLayoutPanel debería tener ahora una fila superior grande, una fila inferior pequeña, una columna izquierda pequeña y una columna derecha grande. Puede cambiar el tamaño de las filas y columnas de TableLayoutPanel eligiendo tableLayoutPanel1 en el formulario y arrastrando sus bordes de fila y columna.

     ![Form1 con TableLayoutPanel cambiado de tamaño](../ide/media/vs-formafterlayoutpanel.png "VS_FormAfterLayoutPanel") Form1 con TableLayoutPanel cambiado de tamaño

### <a name="to-continue-or-review"></a>Para continuar o revisar

- Para ir al siguiente paso del tutorial, vea [paso 5: agregar controles al formulario](../ide/step-5-add-controls-to-your-form.md).

- Para volver al paso anterior del tutorial, vea [paso 3: establecer las propiedades del formulario](../ide/step-3-set-your-form-properties.md).
